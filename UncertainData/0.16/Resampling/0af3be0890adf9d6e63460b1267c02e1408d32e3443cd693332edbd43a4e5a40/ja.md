```
resample(uvd::UVAL_COLLECTION_TYPES, n::Int) -> Vector{Vector{T}}
```

不確実な値データセットの分布に従って、`n` 回の実現を引き出します。

[`UVAL_COLLECTION_TYPES`](@ref) も参照してください。

## 例

```julia
# ガンマ分布で表された不確実な値を生成する
uvals = [UncertainValue(Gamma(i, rand())) for i = 1:100]

# コレクションを一度再サンプリングする
resample(uvals)
```
