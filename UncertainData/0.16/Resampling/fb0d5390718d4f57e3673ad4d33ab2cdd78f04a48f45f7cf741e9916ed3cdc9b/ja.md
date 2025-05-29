```
resample(x::UVAL_COLLECTION_TYPES, constraint::SamplingConstraint, n::Int) -> Vector{Vector{T}} where T
```

`x`（不確実な値のコレクション）を再サンプリングし、`x`内の各不確実な値から1つのランダムな数を引き出します。

[`UVAL_COLLECTION_TYPES`](@ref)も参照してください。

## 例

```julia
# ガンマ分布で表される不確実な値を生成
uvals = [UncertainValue(Gamma(i, rand())) for i = 1:100]

# コレクションを1回再サンプリング
resample(uvals)
```
