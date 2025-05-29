```
MixedModelSummary{T} <: MixedModel{T}
MixedModelSummary(m::LinearMixedModel)
```

Abstract type for a "summary" of a `MixedModel` with a reduced memory footprint.

Concrete subtypes do not the model matrices of a `MixedModel` and thus will consume far less memory, especially for models with many observations. However, they may store relevant parameters and derived values for implementing common `StatsAPI`` methods that don't depend on the original data.

See also [`LinearMixedModelSummary`](@ref)
