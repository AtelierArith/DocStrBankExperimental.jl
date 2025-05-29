```
SegmentedSum{V <: AbstractVector{<:Number}} <: AbstractAggregation
```

[`AbstractAggregation`](@ref) implementing segmented sum aggregation:

$f(\{x_1, \ldots, x_k\}) = \sum_{i = 1}^{k} x_i$

Stores a vector of parameters `ψ` that are filled into the resulting matrix in case an empty bag is encountered.

See also: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
