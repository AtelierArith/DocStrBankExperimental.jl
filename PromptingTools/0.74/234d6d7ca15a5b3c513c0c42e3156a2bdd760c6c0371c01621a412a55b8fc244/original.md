```
aigenerate(prompt_schema::AbstractOpenAISchema, prompt::ALLOWED_PROMPT_TYPE;
    verbose::Bool = true,
    api_key::String = OPENAI_API_KEY,
    model::String = MODEL_CHAT, return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    streamcallback::Any = nothing,
    no_system_message::Bool = false,
    name_user::Union{Nothing, String} = nothing,
    name_assistant::Union{Nothing, String} = nothing,
    http_kwargs::NamedTuple = (retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), api_kwargs::NamedTuple = NamedTuple(),
    kwargs...)
```

Generate an AI response based on a given prompt using the OpenAI API.

# Arguments

  * `prompt_schema`: An optional object to specify which prompt template should be applied (Default to `PROMPT_SCHEMA = OpenAISchema`)
  * `prompt`: Can be a string representing the prompt for the AI conversation, a `UserMessage`, a vector of `AbstractMessage` or an `AITemplate`
  * `verbose`: A boolean indicating whether to print additional information.
  * `api_key`: A string representing the API key for accessing the OpenAI API.
  * `model`: A string representing the model to use for generating the response. Can be an alias corresponding to a model ID defined in `MODEL_ALIASES`.
  * `return_all::Bool=false`: If `true`, returns the entire conversation history, otherwise returns only the last message (the `AIMessage`).
  * `dry_run::Bool=false`: If `true`, skips sending the messages to the model (for debugging, often used with `return_all=true`).
  * `conversation`: An optional vector of `AbstractMessage` objects representing the conversation history. If not provided, it is initialized as an empty vector.
  * `streamcallback`: A callback function to handle streaming responses. Can be simply `stdout` or a `StreamCallback` object. See `?StreamCallback` for details. Note: We configure the `StreamCallback` (and necessary `api_kwargs`) for you, unless you specify the `flavor`. See `?configure_callback!` for details.
  * `no_system_message::Bool=false`: If `true`, the default system message is not included in the conversation history. Any existing system message is converted to a `UserMessage`.
  * `name_user::Union{Nothing, String} = nothing`: The name to use for the user in the conversation history. Defaults to `nothing`.
  * `name_assistant::Union{Nothing, String} = nothing`: The name to use for the assistant in the conversation history. Defaults to `nothing`.
  * `http_kwargs`: A named tuple of HTTP keyword arguments.
  * `api_kwargs`: A named tuple of API keyword arguments. Useful parameters include:

      * `temperature`: A float representing the temperature for sampling (ie, the amount of "creativity"). Often defaults to `0.7`.
      * `logprobs`: A boolean indicating whether to return log probabilities for each token. Defaults to `false`.
      * `n`: An integer representing the number of completions to generate at once (if supported).
      * `stop`: A vector of strings representing the stop conditions for the conversation. Defaults to an empty vector.
  * `kwargs`: Prompt variables to be used to fill the prompt/template

# Returns

If `return_all=false` (default):

  * `msg`: An `AIMessage` object representing the generated AI message, including the content, status, tokens, and elapsed time.

Use `msg.content` to access the extracted string.

If `return_all=true`:

  * `conversation`: A vector of `AbstractMessage` objects representing the conversation history, including the response from the AI model (`AIMessage`).

See also: `ai_str`, `aai_str`, `aiembed`, `aiclassify`, `aiextract`, `aiscan`, `aitemplates`

# Example

Simple hello world to test the API:

```julia
result = aigenerate("Say Hi!")
# [ Info: Tokens: 29 @ Cost: $0.0 in 1.0 seconds
# AIMessage("Hello! How can I assist you today?")
```

`result` is an `AIMessage` object. Access the generated string via `content` property:

```julia
typeof(result) # AIMessage{SubString{String}}
propertynames(result) # (:content, :status, :tokens, :elapsed
result.content # "Hello! How can I assist you today?"
```

___ You can use string interpolation:

```julia
a = 1
msg=aigenerate("What is `$a+$a`?")
msg.content # "The sum of `1+1` is `2`."
```

___ You can provide the whole conversation or more intricate prompts as a `Vector{AbstractMessage}`:

```julia
const PT = PromptingTools

conversation = [
    PT.SystemMessage("You're master Yoda from Star Wars trying to help the user become a Yedi."),
    PT.UserMessage("I have feelings for my iPhone. What should I do?")]
msg=aigenerate(conversation)
# AIMessage("Ah, strong feelings you have for your iPhone. A Jedi's path, this is not... <continues>")
```

Example of streaming:

```julia
# Simplest usage, just provide where to steam the text
msg = aigenerate("Count from 1 to 100."; streamcallback = stdout)

streamcallback = PT.StreamCallback()
msg = aigenerate("Count from 1 to 100."; streamcallback)
# this allows you to inspect each chunk with `streamcallback.chunks`. You can them empty it with `empty!(streamcallback)` in between repeated calls.

# Get verbose output with details of each chunk
streamcallback = PT.StreamCallback(; verbose=true, throw_on_error=true)
msg = aigenerate("Count from 1 to 10."; streamcallback)
```

WARNING: If you provide a `StreamCallback` object, we assume you want to configure everything yourself, so you need to make sure to set `stream = true` in the `api_kwargs`!

Learn more in `?StreamCallback`. Note: Streaming support is only for OpenAI models and it doesn't yet support tool calling and a few other features (logprobs, refusals, etc.)
