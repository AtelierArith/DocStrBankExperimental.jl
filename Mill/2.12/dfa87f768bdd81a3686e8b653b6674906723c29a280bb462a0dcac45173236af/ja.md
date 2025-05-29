```
SegmentedMeanMax([t::Type, ]d::Integer)
```

[`SegmentedMean`](@ref) と [`SegmentedMax`](@ref) 演算子からなる [`AggregationStack`](@ref) を構築します。

# 例

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

関連項目: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref), [`SegmentedSum`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
