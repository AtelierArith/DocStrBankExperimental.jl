```
load_structure!(optimizer::AbstractStructuredOptimizer, structure::AbstractStochasticStructure, x₀::AbstractVector)
```

Instantiate the `optimizer` with the stochastic program represented in memory by the given `structure` and initial decision `x₀`.

See also: [`optimize!`](@ref)
