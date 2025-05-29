```
SegmentedSumMeanMax([t::Type, ]d::Integer)
```

[`SegmentedSum`](@ref)、[`SegmentedMean`](@ref)、および[`SegmentedMax`](@ref)オペレーターで構成される[`AggregationStack`](@ref)を構築します。

# 例

```jldoctest
julia> SegmentedSumMeanMax(4)
AggregationStack:
 SegmentedSum(ψ = Float32[0.0, 0.0, 0.0, 0.0])
 SegmentedMean(ψ = Float32[0.0, 0.0, 0.0, 0.0])
 SegmentedMax(ψ = Float32[0.0, 0.0, 0.0, 0.0])

julia> SegmentedSumMeanMax(Float64, 2)
AggregationStack:
 SegmentedSum(ψ = [0.0, 0.0])
 SegmentedMean(ψ = [0.0, 0.0])
 SegmentedMax(ψ = [0.0, 0.0])
```

関連情報: [`AbstractAggregation`](@ref)、[`AggregationStack`](@ref)、[`SegmentedSum`](@ref)、     [`SegmentedMax`](@ref)、[`SegmentedMean`](@ref)、[`SegmentedPNorm`](@ref)、[`SegmentedLSE`](@ref)。
