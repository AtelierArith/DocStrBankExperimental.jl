```
SegmentedMax{V <: AbstractVector{<:Number}} <: AbstractAggregation
```

[`AbstractAggregation`](@ref) がセグメント最大集約を実装します：

$$
f(\{x_1, \ldots, x_k\}) = \max_{i = 1, \ldots, k} x_i
$$

空のバッグが遭遇した場合に結果の行列に埋め込まれるパラメータ `ψ` のベクトルを格納します。

参照： [`AbstractAggregation`](@ref), [`AggregationStack`](@ref),     [`SegmentedMean`](@ref), [`SegmentedSum`](@ref), [`SegmentedPNorm`](@ref), [`SegmentedLSE`](@ref).
