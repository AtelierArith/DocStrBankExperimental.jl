```
BagCount{T <: AbstractAggregation}
```

A wrapper type that when called applies the [`AbstractAggregation`](@ref) stored in it, and appends one more element containing bag size after $x ↦ \log(x + 1)$ transformation to the result.

Used as a functor:

```
(bc::BagCount)(x, bags[, w])
```

where `x` is either `AbstractMatrix` or `missing`, `bags` is [`AbstractBags`](@ref) structure and optionally `w` is an `AbstractVector` of weights.

# Examples

```jldoctest
julia> x = Float32[0 1 2; 3 4 5]
2×3 Matrix{Float32}:
 0.0  1.0  2.0
 3.0  4.0  5.0

julia> b = bags([1:1, 2:3])
AlignedBags{Int64}(UnitRange{Int64}[1:1, 2:3])

julia> a = vcat(SegmentedMean(2), SegmentedMax(2))
AggregationStack:
 SegmentedMean(ψ = Float32[0.0, 0.0])
 SegmentedMax(ψ = Float32[0.0, 0.0])

julia> a(x, b)
4×2 Matrix{Float32}:
 0.0  1.5
 3.0  4.5
 0.0  2.0
 3.0  5.0

julia> BagCount(a)(x, b)
5×2 Matrix{Float32}:
 0.0       1.5
 3.0       4.5
 0.0       2.0
 3.0       5.0
 0.693147  1.09861
```

See also: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref), [`SegmentedSum`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
