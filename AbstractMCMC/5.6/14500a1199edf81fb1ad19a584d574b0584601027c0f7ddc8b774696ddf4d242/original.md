```
sample(
    rng::Random.AbatractRNG=Random.default_rng(),
    model::AbstractModel,
    sampler::AbstractSampler,
    N_or_isdone;
    kwargs...,
)
```

Sample from the `model` with the Markov chain Monte Carlo `sampler` and return the samples.

If `N_or_isdone` is an `Integer`, exactly `N_or_isdone` samples are returned.

Otherwise, sampling is performed until a convergence criterion `N_or_isdone` returns `true`. The convergence criterion has to be a function with the signature

```julia
isdone(rng, model, sampler, samples, state, iteration; kwargs...)
```

where `state` and `iteration` are the current state and iteration of the sampler, respectively. It should return `true` when sampling should end, and `false` otherwise.

# Keyword arguments

See https://turinglang.org/AbstractMCMC.jl/dev/api/#Common-keyword-arguments for common keyword arguments.
