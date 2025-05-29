```
SegmentedPNorm{V <: AbstractVector{<:AbstractFloat}} <: AbstractAggregation
```

[`AbstractAggregation`](@ref) がセグメント化された p-ノルム集約を実装します：

$$
f(\{x_1, \ldots, x_k\}; p, c) = \left(\frac{1}{k} \sum_{i = 1}^{k} \vert x_i - c \vert ^ {p} \right)^{\frac{1}{p}}
$$

空のバッグが遭遇した場合に結果の行列に埋め込まれるパラメータのベクトル `ψ` を格納し、計算中に使用されるパラメータ `p` と `c` のベクトルを格納します。

関連情報: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedSum`](@ref), [`SegmentedLSE`](@ref).
