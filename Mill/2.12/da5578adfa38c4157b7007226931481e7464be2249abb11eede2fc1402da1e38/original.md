```
SegmentedMax{V <: AbstractVector{<:Number}} <: AbstractAggregation
```

[`AbstractAggregation`](@ref) implementing segmented max aggregation:

$f(\{x_1, \ldots, x_k\}) = \max_{i = 1, \ldots, k} x_i$

Stores a vector of parameters `ψ` that are filled into the resulting matrix in case an empty bag is encountered.

See also: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref),     [`SegmentedMean`](@ref), [`SegmentedSum`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
