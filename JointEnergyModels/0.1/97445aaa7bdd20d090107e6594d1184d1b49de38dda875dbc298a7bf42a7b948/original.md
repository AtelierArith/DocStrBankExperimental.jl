```
generate_conditional_samples(model, rule::Flux.Optimise.AbstractOptimiser, n::Int, y::Int; kwargs...)
```

A convenience function for generating conditional samples for a given model, sampler and sampling rule. If `n` is `missing`, then the sampler's `batch_size` is used. The conditioning value `y` needs to be specified.
