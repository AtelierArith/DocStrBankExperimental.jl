```
GPT3Mixture(;
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

Mixture over [`GPT3GenerativeFunction`](@ref)s with different prompts. Takes in a vector of prompts and a vector of probabilities, and samples from the mixture according to the probabilities. If the probability argument is ommitted, then the mixture is uniform over the prompts.

This is equivalent to writing a `@gen` function which first samples from a  categorical distribution over prompts, then samples a completion to the selected prompt. However, it operates more efficiently by using [`MultiGPT3GF`](@ref) under the hood to make batched API calls.
