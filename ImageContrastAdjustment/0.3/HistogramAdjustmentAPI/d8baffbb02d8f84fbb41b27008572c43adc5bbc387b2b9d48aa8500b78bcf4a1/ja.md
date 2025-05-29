```
adjust_histogram([T::Type,] img, f::AbstractHistogramAdjustmentAlgorithm, args...; kwargs...)
```

画像 `img` のヒストグラムをアルゴリズム `f` を使用して調整します。

# 出力

返される画像 `img_adjusted` は `Array{T}` です。

`T` が指定されていない場合は、推論されます。

# 例

入力画像とアルゴリズムを `adjust_histogram` に単純に渡します。

```julia
img_adjusted = adjust_histogram(img, f)
```

これは「画像 `img` の `adjust_histogram` をアルゴリズム `f` を使用して行う」と読み取れます。

返り値の型を明示的に指定することもできます：

```julia
img_adjusted_float32 = adjust_histogram(Gray{Float32}, img, f)
```

インプレースのヒストグラム調整については [`adjust_histogram!`](@ref) を参照してください。
