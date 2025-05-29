```
SegmentedSum{V <: AbstractVector{<:Number}} <: AbstractAggregation
```

[`AbstractAggregation`](@ref) がセグメント化された合計集約を実装します：

$$
f(\{x_1, \ldots, x_k\}) = \sum_{i = 1}^{k} x_i
$$

空のバッグが遭遇した場合に結果の行列に埋め込まれるパラメータ `ψ` のベクトルを格納します。

参照： [`AbstractAggregation`](@ref), [`AggregationStack`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
