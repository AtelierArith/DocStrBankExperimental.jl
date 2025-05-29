```
aiextract(prompt_schema::AbstractOpenAISchema, prompt::ALLOWED_PROMPT_TYPE;
    return_type::Union{Type, AbstractTool, Vector},
    verbose::Bool = true,
    api_key::String = OPENAI_API_KEY,
    model::String = MODEL_CHAT,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    http_kwargs::NamedTuple = (retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), api_kwargs::NamedTuple = (;
        tool_choice = nothing),
    strict::Union{Nothing, Bool} = nothing,
    kwargs...)
```

Extract required information (defined by a struct **`return_type`**) from the provided prompt by leveraging OpenAI function calling mode.

This is a perfect solution for extracting structured information from text (eg, extract organization names in news articles, etc.)

It's effectively a light wrapper around `aigenerate` call, which requires additional keyword argument `return_type` to be provided  and will enforce the model outputs to adhere to it.

!!! Note: The types must be CONCRETE, it helps with correct conversion to JSON schema and then conversion back to the struct.

# Arguments

  * `prompt_schema`: An optional object to specify which prompt template should be applied (Default to `PROMPT_SCHEMA = OpenAISchema`)
  * `prompt`: Can be a string representing the prompt for the AI conversation, a `UserMessage`, a vector of `AbstractMessage` or an `AITemplate`
  * `return_type`: A **struct** TYPE (or a Tool, vector of Types) representing the the information we want to extract. Do not provide a struct instance, only the type. Alternatively, you can provide a vector of field names and their types (see `?generate_struct` function for the syntax). If the struct has a docstring, it will be provided to the model as well. It's used to enforce structured model outputs or provide more information.
  * `verbose`: A boolean indicating whether to print additional information.
  * `api_key`: A string representing the API key for accessing the OpenAI API.
  * `model`: A string representing the model to use for generating the response. Can be an alias corresponding to a model ID defined in `MODEL_ALIASES`.
  * `return_all::Bool=false`: If `true`, returns the entire conversation history, otherwise returns only the last message (the `AIMessage`).
  * `dry_run::Bool=false`: If `true`, skips sending the messages to the model (for debugging, often used with `return_all=true`).
  * `conversation`: An optional vector of `AbstractMessage` objects representing the conversation history. If not provided, it is initialized as an empty vector.
  * `http_kwargs`: A named tuple of HTTP keyword arguments.
  * `api_kwargs`: A named tuple of API keyword arguments. 

      * `tool_choice`: Specifies which tool to use for the API call. Usually, one of "auto","any","exact" // `nothing` will pick a default.  Defaults to `"exact"` for 1 tool and `"auto"` for many tools, which is a made-up value to enforce the OpenAI requirements if we want one exact function. Providers like Mistral, Together, etc. use `"any"` instead.
  * `strict::Union{Nothing, Bool} = nothing`: A boolean indicating whether to enforce strict generation of the response (supported only for OpenAI models). It has additional latency for the first request. If `nothing`, standard function calling is used.
  * `json_mode::Union{Nothing, Bool} = nothing`: If `json_mode = true`, we use JSON mode for the response (supported only for OpenAI models). If `nothing`, standard function calling is used.   JSON mode is understood to be more creative and smarter than function calling mode, as it's not mascarading as a function call,   but there is extra latency for the first request to produce grammar for constrained sampling.
  * `kwargs`: Prompt variables to be used to fill the prompt/template

# Returns

If `return_all=false` (default):

  * `msg`: An `DataMessage` object representing the extracted data, including the content, status, tokens, and elapsed time.  Use `msg.content` to access the extracted data.

If `return_all=true`:

  * `conversation`: A vector of `AbstractMessage` objects representing the full conversation history, including the response from the AI model (`DataMessage`).

Note: `msg.content` can be a single object (if a single tool is used) or a vector of objects (if multiple tools are used)!

See also: `tool_call_signature`, `MaybeExtract`, `ItemsExtract`, `aigenerate`, `generate_struct`

# Example

Do you want to extract some specific measurements from a text like age, weight and height? You need to define the information you need as a struct (`return_type`):

```
"Person's age, height, and weight."
struct MyMeasurement
    age::Int # required
    height::Union{Int,Nothing} # optional
    weight::Union{Nothing,Float64} # optional
end
msg = aiextract("James is 30, weighs 80kg. He's 180cm tall."; return_type=MyMeasurement)
# PromptingTools.DataMessage(MyMeasurement)
msg.content
# MyMeasurement(30, 180, 80.0)
```

The fields that allow `Nothing` are marked as optional in the schema:

```
msg = aiextract("James is 30."; return_type=MyMeasurement)
# MyMeasurement(30, nothing, nothing)
```

If there are multiple items you want to extract, define a wrapper struct to get a Vector of `MyMeasurement`:

```
struct ManyMeasurements
    measurements::Vector{MyMeasurement}
end

msg = aiextract("James is 30, weighs 80kg. He's 180cm tall. Then Jack is 19 but really tall - over 190!"; return_type=ManyMeasurements)

msg.content.measurements
# 2-element Vector{MyMeasurement}:
#  MyMeasurement(30, 180, 80.0)
#  MyMeasurement(19, 190, nothing)
```

Or you can use the convenience wrapper `ItemsExtract` to extract multiple measurements (zero, one or more):

```julia
using PromptingTools: ItemsExtract

return_type = ItemsExtract{MyMeasurement}
msg = aiextract("James is 30, weighs 80kg. He's 180cm tall. Then Jack is 19 but really tall - over 190!"; return_type)

msg.content.items # see the extracted items
```

Or if you want your extraction to fail gracefully when data isn't found, use `MaybeExtract{T}` wrapper  (this trick is inspired by the Instructor package!):

```
using PromptingTools: MaybeExtract

return_type = MaybeExtract{MyMeasurement}
# Effectively the same as:
# struct MaybeExtract{T}
#     result::Union{T, Nothing} // The result of the extraction
#     error::Bool // true if a result is found, false otherwise
#     message::Union{Nothing, String} // Only present if no result is found, should be short and concise
# end

# If LLM extraction fails, it will return a Dict with `error` and `message` fields instead of the result!
msg = aiextract("Extract measurements from the text: I am giraffe"; return_type)
msg.content
# MaybeExtract{MyMeasurement}(nothing, true, "I'm sorry, but I can only assist with human measurements.")
```

That way, you can handle the error gracefully and get a reason why extraction failed (in `msg.content.message`).

Note that the error message refers to a giraffe not being a human,   because in our `MyMeasurement` docstring, we said that it's for people!

Some non-OpenAI providers require a different specification of the "tool choice" than OpenAI.  For example, to use Mistral models ("mistrall" for mistral large), do:

```julia
"Some fruit"
struct Fruit
    name::String
end
aiextract("I ate an apple",return_type=Fruit,api_kwargs=(;tool_choice="any"),model="mistrall")
# Notice two differences: 1) struct MUST have a docstring, 2) tool_choice is set explicitly set to "any"
```

Example of using a vector of field names with `aiextract`

```julia
fields = [:location, :temperature => Float64, :condition => String]
msg = aiextract("Extract the following information from the text: location, temperature, condition. Text: The weather in New York is sunny and 72.5 degrees Fahrenheit."; return_type = fields)
```

Or simply call `aiextract("some text"; return_type = [:reasoning,:answer])` to get a Chain of Thought reasoning for extraction task.

It will be returned it a new generated type, which you can check with `PromptingTools.isextracted(msg.content) == true` to confirm the data has been extracted correctly.

This new syntax also allows you to provide field-level descriptions, which will be passed to the model.

```julia
fields_with_descriptions = [
    :location,
    :temperature => Float64,
    :temperature__description => "Temperature in degrees Fahrenheit",
    :condition => String,
    :condition__description => "Current weather condition (e.g., sunny, rainy, cloudy)"
]
msg = aiextract("The weather in New York is sunny and 72.5 degrees Fahrenheit."; return_type = fields_with_descriptions)
```

If you feel that the extraction is not smart/creative enough, you can use `json_mode = true` to enforce the JSON mode,  which automatically enables the structured output mode (as opposed to function calling mode).

The JSON mode is useful for cases when you want to enforce a specific output format, such as JSON, and want the model to adhere to that format, but don't want to pretend it's a "function call". Expect a few second delay on the first call for a specific struct, as the provider has to produce the constrained grammer first.

```julia
msg = aiextract("Extract the following information from the text: location, temperature, condition. Text: The weather in New York is sunny and 72.5 degrees Fahrenheit."; 
return_type = fields_with_descriptions, json_mode = true)
# PromptingTools.DataMessage(NamedTuple)

msg.content
# (location = "New York", temperature = 72.5, condition = "sunny")
```

It works equally well for structs provided as return types:

```julia
msg = aiextract("James is 30, weighs 80kg. He's 180cm tall."; return_type=MyMeasurement, json_mode=true)
```
