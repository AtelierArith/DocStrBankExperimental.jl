```
SegmentedSumMax([t::Type, ]d::Integer)
```

Construct [`AggregationStack`](@ref) consisting of [`SegmentedSum`](@ref) and [`SegmentedMax`](@ref) operators.

# Examples

```jldoctest
julia> SegmentedSumMax(4)
AggregationStack:
 SegmentedSum(ψ = Float32[0.0, 0.0, 0.0, 0.0])
 SegmentedMax(ψ = Float32[0.0, 0.0, 0.0, 0.0])

julia> SegmentedSumMax(Float64, 2)
AggregationStack:
 SegmentedSum(ψ = [0.0, 0.0])
 SegmentedMax(ψ = [0.0, 0.0])
```

See also: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref), [`SegmentedSum`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
