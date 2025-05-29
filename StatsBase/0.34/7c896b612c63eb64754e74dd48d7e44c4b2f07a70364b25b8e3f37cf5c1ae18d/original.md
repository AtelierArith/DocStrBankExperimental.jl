```
Weights(vs, wsum=sum(vs))
```

Construct a `Weights` vector with weight values `vs`. A precomputed sum may be provided as `wsum`.

The `Weights` type describes a generic weights vector which does not support all operations possible for [`FrequencyWeights`](@ref), [`AnalyticWeights`](@ref) and [`ProbabilityWeights`](@ref).
