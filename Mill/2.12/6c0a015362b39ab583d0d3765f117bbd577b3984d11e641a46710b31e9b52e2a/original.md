```
SegmentedLSE{V <: AbstractVector{<:AbstractFloat}} <: AbstractAggregation
```

[`AbstractAggregation`](@ref) implementing segmented log-sum-exp (LSE) aggregation:

$f(\{x_1, \ldots, x_k\}; r) = \frac{1}{r}\log \left(\frac{1}{k} \sum_{i = 1}^{k} \exp({r\cdot x_i})\right)$

Stores a vector of parameters `ψ` that are filled into the resulting matrix in case an empty bag is encountered, and a vector of parameters `r` used during computation.

See also: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedSum`](@ref), [`SegmentedPNorm`](@ref).
