```
SegmentedMeanMax([t::Type, ]d::Integer)
```

Construct [`AggregationStack`](@ref) consisting of [`SegmentedMean`](@ref) and [`SegmentedMax`](@ref) operators.

# Examples

```jldoctest
julia> SegmentedMeanMax(4)
AggregationStack:
 SegmentedMean(ψ = Float32[0.0, 0.0, 0.0, 0.0])
 SegmentedMax(ψ = Float32[0.0, 0.0, 0.0, 0.0])

julia> SegmentedMeanMax(Float64, 2)
AggregationStack:
 SegmentedMean(ψ = [0.0, 0.0])
 SegmentedMax(ψ = [0.0, 0.0])
```

See also: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref), [`SegmentedSum`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
