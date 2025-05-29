```
sample(
    rng::Random.AbstractRNG=Random.default_rng(),
    logdensity,
    sampler::AbstractSampler,
    N_or_isdone;
    kwargs...,
)
```

Wrap the `logdensity` function in a [`LogDensityModel`](@ref), and call `sample` with the resulting model instead of `logdensity`.

The `logdensity` function has to support the [LogDensityProblems.jl](https://github.com/tpapp/LogDensityProblems.jl) interface.
