```
aigenerate(prompt_schema::AbstractAnthropicSchema, prompt::ALLOWED_PROMPT_TYPE; verbose::Bool = true,
    api_key::String = ANTHROPIC_API_KEY, model::String = MODEL_CHAT,
    return_all::Bool = false, dry_run::Bool = false,
    conversation::AbstractVector{<:AbstractMessage} = AbstractMessage[],
    streamcallback::Any = nothing,
    no_system_message::Bool = false,
    aiprefill::Union{Nothing, AbstractString} = nothing,
    http_kwargs::NamedTuple = NamedTuple(), api_kwargs::NamedTuple = NamedTuple(),
    cache::Union{Nothing, Symbol} = nothing,
    betas::Union{Nothing, Vector{Symbol}} = nothing,
    kwargs...)
```

Generate an AI response based on a given prompt using the Anthropic API.

# Arguments

  * `prompt_schema`: An optional object to specify which prompt template should be applied (Default to `PROMPT_SCHEMA = OpenAISchema` not `AbstractAnthropicSchema`)
  * `prompt`: Can be a string representing the prompt for the AI conversation, a `UserMessage`, a vector of `AbstractMessage` or an `AITemplate`
  * `verbose`: A boolean indicating whether to print additional information.
  * `api_key`: API key for the Antropic API. Defaults to `ANTHROPIC_API_KEY` (loaded via `ENV["ANTHROPIC_API_KEY"]`).
  * `model`: A string representing the model to use for generating the response. Can be an alias corresponding to a model ID defined in `MODEL_ALIASES`, eg, "claudeh".
  * `return_all::Bool=false`: If `true`, returns the entire conversation history, otherwise returns only the last message (the `AIMessage`).
  * `dry_run::Bool=false`: If `true`, skips sending the messages to the model (for debugging, often used with `return_all=true`).
  * `conversation::AbstractVector{<:AbstractMessage}=[]`: Not allowed for this schema. Provided only for compatibility.
  * `streamcallback::Any`: A callback function to handle streaming responses. Can be simply `stdout` or `StreamCallback` object. See `?StreamCallback` for details. Note: We configure the `StreamCallback` (and necessary `api_kwargs`) for you, unless you specify the `flavor`. See `?configure_callback!` for details.
  * `no_system_message::Bool=false`: If `true`, do not include the default system message in the conversation history OR convert any provided system message to a user message.
  * `aiprefill::Union{Nothing, AbstractString}`: A string to be used as a prefill for the AI response. This steer the AI response in a certain direction (and potentially save output tokens). It MUST NOT end with a trailing with space. Useful for JSON formatting.
  * `http_kwargs::NamedTuple`: Additional keyword arguments for the HTTP request. Defaults to empty `NamedTuple`.
  * `api_kwargs::NamedTuple`: Additional keyword arguments for the Ollama API. Defaults to an empty `NamedTuple`.

      * `max_tokens::Int`: The maximum number of tokens to generate. Defaults to 2048, because it's a required parameter for the API.
  * `cache`: A symbol representing the caching strategy to be used. Currently only `nothing` (no caching), `:system`, `:tools`,`:last`, `:all_but_last` and `:all` are supported. Note that COST estimate will be wrong (ignores the caching).

      * `:system`: Mark only the system message as cacheable. Best default if you have large system message and you will be sending short conversations (no replies / multi-turn conversations).
      * `:all`: Mark SYSTEM, one before last and LAST user message as cacheable. Best for multi-turn conversations (you write cache point as "last" and it will be read in the next turn as "preceding" cache mark).
      * `:last`: Mark only the last message as cacheable. Use ONLY if you want to send the SAME REQUEST multiple times (and want to save upto the last USER message). This will not work for multi-turn conversations, as the "last" message keeps moving.
      * `:all_but_last`: Mark SYSTEM and one before LAST USER message. Use if you have a longer conversation that you want to re-use, but you will NOT CONTINUE it (no subsequent messages/follow-ups).
      * In short, use `:all` for multi-turn conversations, `:system` for repeated single-turn conversations with same system message, and `:all_but_last` for longer conversations that you want to re-use, but not continue.
  * `betas::Union{Nothing, Vector{Symbol}}`: A vector of symbols representing the beta features to be used. See `?anthropic_extra_headers` for details.
  * `kwargs`: Prompt variables to be used to fill the prompt/template

Note: At the moment, the cache is only allowed for prompt segments over 1024 tokens (in some cases, over 2048 tokens). You'll get an error if you try to cache short prompts.

# Returns

  * `msg`: An `AIMessage` object representing the generated AI message, including the content, status, tokens, and elapsed time.

Use `msg.content` to access the extracted string.

See also: `ai_str`, `aai_str`

# Example

Simple hello world to test the API:

```julia
const PT = PromptingTools
schema = PT.AnthropicSchema() # We need to explicit if we want Anthropic, otherwise OpenAISchema is the default

msg = aigenerate(schema, "Say hi!"; model="claudeh") #claudeh is the model alias for Claude 3 Haiku, fast and cheap model
[ Info: Tokens: 21 @ Cost: $0.0 in 0.6 seconds
AIMessage("Hello!")
```

`msg` is an `AIMessage` object. Access the generated string via `content` property:

```julia
typeof(msg) # AIMessage{SubString{String}}
propertynames(msg) # (:content, :status, :tokens, :elapsed, :cost, :log_prob, :finish_reason, :run_id, :sample_id, :_type)
msg.content # "Hello!
```

Note: We need to be explicit about the schema we want to use. If we don't, it will default to `OpenAISchema` (=`PT.DEFAULT_SCHEMA`) Alternatively, if you provide a known model name or alias (eg, `claudeh` for Claude 3 Haiku - see `MODEL_REGISTRY`), the schema will be inferred from the model name.

We will use Claude 3 Haiku model for the following examples, so not need to specify the schema. See also "claudeo" and "claudes" for other Claude 3 models.

You can use string interpolation:

```julia
const PT = PromptingTools

a = 1
msg=aigenerate("What is `$a+$a`?"; model="claudeh")
msg.content # "The answer to `1+1` is `2`."
```

___ You can provide the whole conversation or more intricate prompts as a `Vector{AbstractMessage}`. Claude models are good at completeling conversations that ended with an `AIMessage` (they just continue where it left off):

```julia
const PT = PromptingTools

conversation = [
    PT.SystemMessage("You're master Yoda from Star Wars trying to help the user become a Yedi."),
    PT.UserMessage("I have feelings for my iPhone. What should I do?"),
    PT.AIMessage("Hmm, strong the attachment is,")]

msg = aigenerate(conversation; model="claudeh")
AIMessage("I sense. But unhealthy it may be. Your iPhone, a tool it is, not a living being. Feelings of affection, understandable they are, <continues>")
```

Example of streaming:

```julia
# Simplest usage, just provide where to steam the text
msg = aigenerate("Count from 1 to 100."; streamcallback = stdout, model="claudeh")

streamcallback = PT.StreamCallback()
msg = aigenerate("Count from 1 to 100."; streamcallback, model="claudeh")
# this allows you to inspect each chunk with `streamcallback.chunks`. You can them empty it with `empty!(streamcallback)` in between repeated calls.

# Get verbose output with details of each chunk
streamcallback = PT.StreamCallback(; verbose=true, throw_on_error=true)
msg = aigenerate("Count from 1 to 10."; streamcallback, model="claudeh")
```

Note: Streaming support is only for Anthropic models and it doesn't yet support tool calling and a few other features (logprobs, refusals, etc.)

You can also provide a prefill for the AI response to steer the response in a certain direction (eg, formatting, style):

```julia
msg = aigenerate("Sum up 1 to 100."; aiprefill = "I'd be happy to answer in one number without any additional text. The answer is:", model="claudeh")
```

Note: It MUST NOT end with a trailing with space. You'll get an API error if you do.
