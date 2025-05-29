```
SegmentedPNorm{V <: AbstractVector{<:AbstractFloat}} <: AbstractAggregation
```

[`AbstractAggregation`](@ref) implementing segmented p-norm aggregation:

$f(\{x_1, \ldots, x_k\}; p, c) = \left(\frac{1}{k} \sum_{i = 1}^{k} \vert x_i - c \vert ^ {p} \right)^{\frac{1}{p}}$

Stores a vector of parameters `ψ` that are filled into the resulting matrix in case an empty bag is encountered, and vectors of parameters `p` and `c` used during computation.

See also: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedSum`](@ref), [`SegmentedLSE`](@ref).
