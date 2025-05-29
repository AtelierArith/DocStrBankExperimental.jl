```
MultiGPT3GenerativeFunction(;
    model = "davinci-002",
    temperature = 1.0,
    max_tokens = 1024,
    stop = nothing,
    batch_size = 10,
    encoding = GenGPT3.MODEL_ENCODINGS[model],
    api_key_lookup = () -> ENV["OPENAI_API_KEY"],
    organization_lookup = () -> ENV["OPENAI_ORGANIZATION"]
)
```

Batched version of [`GPT3GenerativeFunction`](@ref), which requests and  returns completions for a batch of prompts. Takes in a `Vector` of `String` valued prompts as an argument. The completion for the `i`th prompt is stored in the `i => output` address of the resulting trace.
