```
load_model!(optimizer::AbstractSampledOptimizer, model::StochasticModel, x₀::AbstractVector)
```

Instantiate the `optimizer` with the stochastic model and initial decision `x₀`.

See also: [`optimize!`](@ref)
