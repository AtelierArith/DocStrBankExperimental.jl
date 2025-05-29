```
aiextract(prompt_schema::AbstractAnthropicSchema, prompt::ALLOWED_PROMPT_TYPE;
    return_type::Union{Type, AbstractTool, Vector},
    verbose::Bool = true,
    api_key::String = ANTHROPIC_API_KEY,
    model::String = MODEL_CHAT,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    no_system_message::Bool = false,
    http_kwargs::NamedTuple = (retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), api_kwargs::NamedTuple = NamedTuple(),
    cache::Union{Nothing, Symbol} = nothing,
    betas::Union{Nothing, Vector{Symbol}} = nothing,
    kwargs...)
```

Extract required information (defined by a struct **`return_type`**) from the provided prompt by leveraging Anthropic's function calling mode.

This is a perfect solution for extracting structured information from text (eg, extract organization names in news articles, etc.).

Read best practics [here](https://docs.anthropic.com/claude/docs/tool-use#tool-use-best-practices-and-limitations).

It's effectively a light wrapper around `aigenerate` call, which requires additional keyword argument `return_type` to be provided  and will enforce the model outputs to adhere to it.

# Arguments

  * `prompt_schema`: An optional object to specify which prompt template should be applied (Default to `PROMPT_SCHEMA = OpenAISchema`)
  * `prompt`: Can be a string representing the prompt for the AI conversation, a `UserMessage`, a vector of `AbstractMessage` or an `AITemplate`
  * `return_type`: A **struct** TYPE representing the the information we want to extract. Do not provide a struct instance, only the type. If the struct has a docstring, it will be provided to the model as well. It's used to enforce structured model outputs or provide more information. Alternatively, you can provide a vector of field names and their types (see `?generate_struct` function for the syntax).
  * `verbose`: A boolean indicating whether to print additional information.
  * `api_key`: A string representing the API key for accessing the OpenAI API.
  * `model`: A string representing the model to use for generating the response. Can be an alias corresponding to a model ID defined in `MODEL_ALIASES`.
  * `return_all::Bool=false`: If `true`, returns the entire conversation history, otherwise returns only the last message (the `AIMessage`).
  * `dry_run::Bool=false`: If `true`, skips sending the messages to the model (for debugging, often used with `return_all=true`).
  * `conversation`: An optional vector of `AbstractMessage` objects representing the conversation history. If not provided, it is initialized as an empty vector.
  * `no_system_message::Bool = false`: If `true`, skips the system message in the conversation history.
  * `http_kwargs`: A named tuple of HTTP keyword arguments.
  * `api_kwargs`: A named tuple of API keyword arguments. 

      * `:tool_choice`: A string indicating which tool to use. Supported values are `nothing`, `"auto"`, `"any"` and `"exact"`. `nothing` will use the default tool choice.
  * `cache`: A symbol representing the caching strategy to be used. Currently only `nothing` (no caching), `:system`, `:tools`,`:last`, `:all_but_last`, and `:all` are supported. Note: COST estimate will be wrong (ignores the caching).

      * `:system`: Mark only the system message as cacheable. Best default if you have large system message and you will be sending short conversations (no replies / multi-turn conversations).
      * `:all`: Mark SYSTEM, one before last and LAST user message as cacheable. Best for multi-turn conversations (you write cache point as "last" and it will be read in the next turn as "preceding" cache mark).
      * `:last`: Mark only the last message as cacheable. Use ONLY if you want to send the SAME REQUEST multiple times (and want to save upto the last USER message). This will not work for multi-turn conversations, as the "last" message keeps moving.
      * `:all_but_last`: Mark SYSTEM and one before LAST USER message. Use if you have a longer conversation that you want to re-use, but you will NOT CONTINUE it (no subsequent messages/follow-ups).
      * In short, use `:all` for multi-turn conversations, `:system` for repeated single-turn conversations with same system message, and `:all_but_last` for longer conversations that you want to re-use, but not continue.
  * `betas::Union{Nothing, Vector{Symbol}}`: A vector of symbols representing the beta features to be used. See `?anthropic_extra_headers` for details.
  * `kwargs`: Prompt variables to be used to fill the prompt/template

Note: At the moment, the cache is only allowed for prompt segments over 1024 tokens (in some cases, over 2048 tokens). You'll get an error if you try to cache short prompts.

# Returns

If `return_all=false` (default):

  * `msg`: An `DataMessage` object representing the extracted data, including the content, status, tokens, and elapsed time.  Use `msg.content` to access the extracted data.

If `return_all=true`:

  * `conversation`: A vector of `AbstractMessage` objects representing the full conversation history, including the response from the AI model (`DataMessage`).

See also: `tool_call_signature`, `MaybeExtract`, `ItemsExtract`, `aigenerate`

# Example

Do you want to extract some specific measurements from a text like age, weight and height? You need to define the information you need as a struct (`return_type`):

```
"Person's age, height, and weight."
struct MyMeasurement
    age::Int # required
    height::Union{Int,Nothing} # optional
    weight::Union{Nothing,Float64} # optional
end
msg = aiextract("James is 30, weighs 80kg. He's 180cm tall."; model="claudeh", return_type=MyMeasurement)
# PromptingTools.DataMessage(MyMeasurement)
msg.content
# MyMeasurement(30, 180, 80.0)
```

The fields that allow `Nothing` are marked as optional in the schema:

```
msg = aiextract("James is 30."; model="claudeh", return_type=MyMeasurement)
# MyMeasurement(30, nothing, nothing)
```

If there are multiple items you want to extract, define a wrapper struct to get a Vector of `MyMeasurement`:

```
struct ManyMeasurements
    measurements::Vector{MyMeasurement}
end

msg = aiextract("James is 30, weighs 80kg. He's 180cm tall. Then Jack is 19 but really tall - over 190!"; model="claudeh", return_type=ManyMeasurements)

msg.content.measurements
# 2-element Vector{MyMeasurement}:
#  MyMeasurement(30, 180, 80.0)
#  MyMeasurement(19, 190, nothing)
```

Or you can use the convenience wrapper `ItemsExtract` to extract multiple measurements (zero, one or more):

```julia
using PromptingTools: ItemsExtract

return_type = ItemsExtract{MyMeasurement}
msg = aiextract("James is 30, weighs 80kg. He's 180cm tall. Then Jack is 19 but really tall - over 190!"; model="claudeh", return_type)

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
msg = aiextract("Extract measurements from the text: I am giraffe"; model="claudeo", return_type)
msg.content
# Output: MaybeExtract{MyMeasurement}(nothing, true, "I'm sorry, but your input of "I am giraffe" does not contain any information about a person's age, height or weight measurements that I can extract. To use this tool, please provide a statement that includes at least the person's age, and optionally their height in inches and weight in pounds. Without that information, I am unable to extract the requested measurements.")
```

That way, you can handle the error gracefully and get a reason why extraction failed (in `msg.content.message`).

However, this can fail with weaker models like `claudeh`, so we can apply some of our prompt templates with embedding reasoning step:

```julia
msg = aiextract(:ExtractDataCoTXML; data="I am giraffe", model="claudeh", return_type)
msg.content
# Output: MaybeExtract{MyMeasurement}(nothing, true, "The provided data does not contain the expected information about a person's age, height, and weight.")
```

Note that when using a prompt template, we provide `data` for the extraction as the corresponding placeholder (see `aitemplates("extract")` for documentation of this template).

Note that the error message refers to a giraffe not being a human,   because in our `MyMeasurement` docstring, we said that it's for people!

Example of using a vector of field names with `aiextract`

```julia
fields = [:location, :temperature => Float64, :condition => String]
msg = aiextract("Extract the following information from the text: location, temperature, condition. Text: The weather in New York is sunny and 72.5 degrees Fahrenheit."; 
return_type = fields, model="claudeh")
```

Or simply call `aiextract("some text"; return_type = [:reasoning,:answer], model="claudeh")` to get a Chain of Thought reasoning for extraction task.

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
msg = aiextract("The weather in New York is sunny and 72.5 degrees Fahrenheit."; return_type = fields_with_descriptions, model="claudeh")
```
