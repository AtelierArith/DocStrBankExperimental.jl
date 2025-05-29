```
sample(
    rng::Random.AbstractRNG=Random.default_rng(),
    model::AbstractModel,
    sampler::AbstractSampler,
    parallel::AbstractMCMCEnsemble,
    N::Integer,
    nchains::Integer;
    kwargs...,
)
```

Sample `nchains` Monte Carlo Markov chains from the `model` with the `sampler` in parallel using the `parallel` algorithm, and combine them into a single chain.

# Keyword arguments

See https://turinglang.org/AbstractMCMC.jl/dev/api/#Common-keyword-arguments for common keyword arguments.
