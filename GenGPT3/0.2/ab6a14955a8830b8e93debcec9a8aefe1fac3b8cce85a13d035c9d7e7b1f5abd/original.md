```
GPT3ImportanceSampler(;
    model_gf::MultiGPT3GF = MultiGPT3GF(),
    proposal_gf::MultiGPT3GF = model_gf,
    validator::V = nothing,
    max_samples::Union{Int, Nothing} = nothing,
    cache_traces::Bool = false,
)
```

A generative function that performs importance sampling from a GPT-3 model using [`MultiGPT3GF`](@ref) generative functions as the model and the proposal. Called with arguments `(n_samples, model_prompt, proposal_prompt)`, where `n_samples` is the number of samples to draw, `model_prompt` is the prompt to use for the model, and `proposal_prompt` is the prompt to use for the proposal.

After `n_samples` samples are drawn from the proposal, the model is used to  score each sample, and importance weights are computed. A single sample is then chosen according to the importance weights, which is returned as the output of the generative function. Both the `output` and `chosen` index are part of the trace's choicemap.

# Arguments

  * `model_gf::MultiGPT3GF`: The generative function to use for the model.
  * `proposal_gf::MultiGPT3GF`: The generative function to use for the proposal.
  * `validator`: A validator function to use for the sample outputs. If provided,   samples will be drawn until the number of valid samples is equal to   `n_samples`. If set to `nothing`, no validation is performed.
  * `max_samples::Union{Int, Nothing}`: The maximum number of samples to draw   from the proposal if validation is enabled. If set to `nothing`, no maximum   is enforced.
  * `cache_traces::Bool`: Whether to cache traces. If set to `true`, traces will   be cached in a dictionary, and reused if the same arguments are provided.
