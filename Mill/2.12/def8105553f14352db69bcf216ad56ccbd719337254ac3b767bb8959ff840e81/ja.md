```
SegmentedSumMax([t::Type, ]d::Integer)
```

[`SegmentedSum`](@ref) と [`SegmentedMax`](@ref) 演算子からなる [`AggregationStack`](@ref) を構築します。

# 例

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

参照: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref), [`SegmentedSum`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
