```
VRP(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler; confidence = 0.95)
```

Return a confidence interval around the **value of the recouse problem** (`VRP`) of `stochasticmodel` to the given `confidence` level.

If a sample-based optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`EVPI`](@ref), [`VSS`](@ref), [`EWS`](@ref)
