```
optimize!(stochasticmodel::StochasticModel, sampler::AbstractSampler; crash::AbstractCrash = Crash.None(), kw...)
```

Approximately optimize the `stochasticmodel` when the underlying scenario distribution is inferred by `sampler`. If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.
