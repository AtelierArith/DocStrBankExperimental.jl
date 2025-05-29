```
out = detect_edges([T::Type,] img, f::AbstractEdgeDetectionAlgorithm, args...; kwargs...)
```

画像 `img` のエッジをアルゴリズム `f` を使用して検出します。指定されていない場合、`f` は [`Canny`](@ref ImageEdgeDetection.Canny) であると仮定されます。

# 出力

返される画像 `out` は `Array{T}` です。`T` が指定されていない場合は、推測されます。

# 例

入力画像とアルゴリズムを `detect_edges` に渡すだけです。

```julia
f = Canny(spatial_scale = 1.4)
img_edges = detect_edges(img, f)
```

これは「アルゴリズム `f` を使用して画像 `img` の `detect_edges`」と読み取れます。

返り値の型を明示的に指定することもできます：

```julia
f = Canny(spatial_scale = 1.4)
img_edges_float32 = detect_edges(Gray{Float32}, img, f)
```

インプレースエッジ検出については [`detect_edges!`](@ref) も参照してください。
