```
GPT3GenerativeFunction(;
    model = "davinci-002",
    temperature = 1.0,
    max_tokens = 1024,
    stop = nothing,
    encoding = GenGPT3.MODEL_ENCODINGS[model],
    api_key_lookup = () -> ENV["OPENAI_API_KEY"],
    organization_lookup = () -> ENV["OPENAI_ORGANIZATION"]
)
```

Constructs GPT-3 as a generative function, where sampling and scoring of completions are performed via calls to the OpenAI API.

The generative function takes in a prompt as an (optional) argument, then samples and returns a completion. This represents a distribution over strings (up to `max_tokens` long) which end in a `stop` sequence. The completion is stored in the `output` address of the resulting trace.

# Arguments

  * `model::String`:   The pretrained model to query. Defaults to `"davinci-002"`.
  * `temperature::Float64 = 1.0`:   The softmax temperature. Values between `0.0``and`2.0`are allowed.   Higher temperatures increase randomness. Note that if this is not set   to`1.0`, then the resulting log probabilities will no longer be normalized.
  * `max_tokens::Int = 1024`:   The maximum number of output tokens generated (including the stop sequence).
  * `encoding::String = GenGPT3.MODEL_ENCODINGS[model]`:   Tokenizer encoding for the model. For most models, this is `"cl100k_base"`.
  * `stop::Union{String,Nothing} = nothing`:   The stop sequence as a string. Defaults to the `<|endoftext|>` token if not   specified. If specified, then the model will be prevented from generating   any `<|endoftext|>` tokens (to avoid multiple termination possibilities).
  * `api_key_lookup::Function`:   A zero-argument function that returns the OpenAI API key to use. Defaults to   looking up the `"OPENAI_API_KEY"` environment variable.
  * `organization_lookup::Function`:   A zero-argument function that returns the OpenAI organization ID to use.   Defaults to the `"OPENAI_ORGANIZATION"` environment variable, if specified.
