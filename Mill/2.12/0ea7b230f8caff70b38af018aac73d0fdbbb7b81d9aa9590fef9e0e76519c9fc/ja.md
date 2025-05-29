```
SegmentedSumMean([t::Type, ]d::Integer)
```

[`SegmentedSum`](@ref) と [`SegmentedMean`](@ref) 演算子からなる [`AggregationStack`](@ref) を構築します。

# 例

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

参照: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref), [`SegmentedSum`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
