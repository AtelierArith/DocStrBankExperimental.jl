```
aigenerate(prompt_schema::AbstractOllamaManagedSchema, prompt::ALLOWED_PROMPT_TYPE; verbose::Bool = true,
    api_key::String = "", model::String = MODEL_CHAT,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    streamcallback::Any = nothing,
    http_kwargs::NamedTuple = NamedTuple(), api_kwargs::NamedTuple = NamedTuple(),
    kwargs...)
```

Generate an AI response based on a given prompt using the OpenAI API.

# Arguments

  * `prompt_schema`: An optional object to specify which prompt template should be applied (Default to `PROMPT_SCHEMA = OpenAISchema` not `AbstractManagedSchema`)
  * `prompt`: Can be a string representing the prompt for the AI conversation, a `UserMessage`, a vector of `AbstractMessage` or an `AITemplate`
  * `verbose`: A boolean indicating whether to print additional information.
  * `api_key`: Provided for interface consistency. Not needed for locally hosted Ollama.
  * `model`: A string representing the model to use for generating the response. Can be an alias corresponding to a model ID defined in `MODEL_ALIASES`.
  * `return_all::Bool=false`: If `true`, returns the entire conversation history, otherwise returns only the last message (the `AIMessage`).
  * `dry_run::Bool=false`: If `true`, skips sending the messages to the model (for debugging, often used with `return_all=true`).
  * `conversation::AbstractVector{<:AbstractMessage}=[]`: Not allowed for this schema. Provided only for compatibility.
  * `streamcallback::Any`: Just for compatibility. Not supported for this schema.
  * `http_kwargs::NamedTuple`: Additional keyword arguments for the HTTP request. Defaults to empty `NamedTuple`.
  * `api_kwargs::NamedTuple`: Additional keyword arguments for the Ollama API. Defaults to an empty `NamedTuple`.
  * `kwargs`: Prompt variables to be used to fill the prompt/template

# Returns

  * `msg`: An `AIMessage` object representing the generated AI message, including the content, status, tokens, and elapsed time.

Use `msg.content` to access the extracted string.

See also: `ai_str`, `aai_str`, `aiembed`

# Example

Simple hello world to test the API:

```julia
const PT = PromptingTools
schema = PT.OllamaManagedSchema() # We need to explicit if we want Ollama, OpenAISchema is the default

msg = aigenerate(schema, "Say hi!"; model="openhermes2.5-mistral")
# [ Info: Tokens: 69 in 0.9 seconds
# AIMessage("Hello! How can I assist you today?")
```

`msg` is an `AIMessage` object. Access the generated string via `content` property:

```julia
typeof(msg) # AIMessage{SubString{String}}
propertynames(msg) # (:content, :status, :tokens, :elapsed
msg.content # "Hello! How can I assist you today?"
```

Note: We need to be explicit about the schema we want to use. If we don't, it will default to `OpenAISchema` (=`PT.DEFAULT_SCHEMA`) ___ You can use string interpolation:

```julia
const PT = PromptingTools
schema = PT.OllamaManagedSchema()
a = 1
msg=aigenerate(schema, "What is `$a+$a`?"; model="openhermes2.5-mistral")
msg.content # "The result of `1+1` is `2`."
```

___ You can provide the whole conversation or more intricate prompts as a `Vector{AbstractMessage}`:

```julia
const PT = PromptingTools
schema = PT.OllamaManagedSchema()

conversation = [
    PT.SystemMessage("You're master Yoda from Star Wars trying to help the user become a Yedi."),
    PT.UserMessage("I have feelings for my iPhone. What should I do?")]

msg = aigenerate(schema, conversation; model="openhermes2.5-mistral")
# [ Info: Tokens: 111 in 2.1 seconds
# AIMessage("Strong the attachment is, it leads to suffering it may. Focus on the force within you must, ...<continues>")
```

Note: Managed Ollama currently supports at most 1 User Message and 1 System Message given the API limitations. If you want more, you need to use the `ChatMLSchema`.
