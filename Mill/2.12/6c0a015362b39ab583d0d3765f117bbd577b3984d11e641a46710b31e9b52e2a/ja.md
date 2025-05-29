```
SegmentedLSE{V <: AbstractVector{<:AbstractFloat}} <: AbstractAggregation
```

[`AbstractAggregation`](@ref) がセグメント化されたログサム指数 (LSE) 集約を実装します：

$$
f(\{x_1, \ldots, x_k\}; r) = \frac{1}{r}\log \left(\frac{1}{k} \sum_{i = 1}^{k} \exp({r\cdot x_i})\right)
$$

空のバッグが遭遇した場合に結果の行列に埋め込まれるパラメータのベクトル `ψ` と、計算中に使用されるパラメータのベクトル `r` を格納します。

関連項目: [`AbstractAggregation`](@ref), [`AggregationStack`](@ref),     [`SegmentedMax`](@ref), [`SegmentedMean`](@ref), [`SegmentedSum`](@ref), [`SegmentedPNorm`](@ref).
