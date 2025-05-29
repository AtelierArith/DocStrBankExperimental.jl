```
SegmentedSumMean([t::Type, ]d::Integer)
```

Construct [`AggregationStack`](@ref) consisting of [`SegmentedSum`](@ref) and [`SegmentedMean`](@ref) operators.

# Examples

```jldoctest
julia> SegmentedSumMean(4)
AggregationStack:
 SegmentedSum(ψ = Float32[0.0, 0.0, 0.0, 0.0])
 SegmentedMean(ψ = Float32[0.0, 0.0, 0.0, 0.0])

julia> SegmentedSumMean(Float64, 2)
AggregationStack:
 SegmentedSum(ψ = [0.0, 0.0])
 SegmentedMean(ψ = [0.0, 0.0])
```

See also: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref), [`SegmentedSum`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
