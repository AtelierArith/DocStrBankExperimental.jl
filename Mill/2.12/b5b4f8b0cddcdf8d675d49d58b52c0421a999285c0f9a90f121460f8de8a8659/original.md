```
SegmentedMean{V <: AbstractVector{<:Number}}} <: AbstractAggregation
```

[`AbstractAggregation`](@ref) implementing segmented mean aggregation:

$f(\{x_1, \ldots, x_k\}) = \frac{1}{k} \sum_{i = 1}^{k} x_i$

Stores a vector of parameters `ψ` that are filled into the resulting matrix in case an empty bag is encountered.

See also: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref),     [`SegmentedMax`](@ref), [`SegmentedSum`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
