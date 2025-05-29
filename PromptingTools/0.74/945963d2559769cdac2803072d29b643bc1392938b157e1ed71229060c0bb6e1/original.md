```
aigenerate(prompt_schema::AbstractGoogleSchema, prompt::ALLOWED_PROMPT_TYPE;
    verbose::Bool = true,
    api_key::String = GOOGLE_API_KEY,
    model::String = "gemini-pro", return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    no_system_message::Bool = false,
    http_kwargs::NamedTuple = (retry_non_idempotent = true,
        retries = 5,
        readtimeout = 120), api_kwargs::NamedTuple = NamedTuple(),
    kwargs...)
```

Generate an AI response based on a given prompt using the Google Gemini API. Get the API key [here](https://ai.google.dev/).

Note: 

  * There is no "cost" reported as of February 2024, as all access seems to be free-of-charge. See the details [here](https://ai.google.dev/pricing).
  * `tokens` in the returned AIMessage are actually characters, not tokens. We use a *conservative* estimate as they are not provided by the API yet.

# Arguments

  * `prompt_schema`: An optional object to specify which prompt template should be applied (Default to `PROMPT_SCHEMA = OpenAISchema`)
  * `prompt`: Can be a string representing the prompt for the AI conversation, a `UserMessage`, a vector of `AbstractMessage` or an `AITemplate`
  * `verbose`: A boolean indicating whether to print additional information.
  * `api_key`: A string representing the API key for accessing the OpenAI API.
  * `model`: A string representing the model to use for generating the response. Can be an alias corresponding to a model ID defined in `MODEL_ALIASES`. Defaults to
  * `return_all::Bool=false`: If `true`, returns the entire conversation history, otherwise returns only the last message (the `AIMessage`).
  * `dry_run::Bool=false`: If `true`, skips sending the messages to the model (for debugging, often used with `return_all=true`).
  * `conversation`: An optional vector of `AbstractMessage` objects representing the conversation history. If not provided, it is initialized as an empty vector.
  * `no_system_message::Bool=false`: If `true`, do not include the default system message in the conversation history OR convert any provided system message to a user message.
  * `http_kwargs`: A named tuple of HTTP keyword arguments.
  * `api_kwargs`: A named tuple of API keyword arguments.
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
result = aigenerate("Say Hi!"; model="gemini-pro")
# AIMessage("Hi there! 👋 I'm here to help you with any questions or tasks you may have. Just let me know what you need, and I'll do my best to assist you.")
```

`result` is an `AIMessage` object. Access the generated string via `content` property:

```julia
typeof(result) # AIMessage{SubString{String}}
propertynames(result) # (:content, :status, :tokens, :elapsed
result.content # "Hi there! ...
```

___ You can use string interpolation and alias "gemini":

```julia
a = 1
msg=aigenerate("What is `$a+$a`?"; model="gemini")
msg.content # "1+1 is 2."
```

___ You can provide the whole conversation or more intricate prompts as a `Vector{AbstractMessage}`:

```julia
const PT = PromptingTools

conversation = [
    PT.SystemMessage("You're master Yoda from Star Wars trying to help the user become a Yedi."),
    PT.UserMessage("I have feelings for my iPhone. What should I do?")]
msg=aigenerate(conversation; model="gemini")
# AIMessage("Young Padawan, you have stumbled into a dangerous path.... <continues>")
```
