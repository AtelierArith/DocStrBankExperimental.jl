```
out₁, out₂ = detect_subpixel_edges([T₁::Type, T₂::Type], img, f::AbstractEdgeDetectionAlgorithm, args...; kwargs...)
```

画像 `img` のエッジをサブピクセル精度で検出するためにアルゴリズム `f` を使用します。指定されていない場合、`f` は [`Canny`](@ref ImageEdgeDetection.Canny) であると見なされます。

# 出力

エッジの整数成分は、`out₁` の非ゼロ行および列エントリに対応し、これは `Array{T₁}` です。対応するサブピクセルオフセットは、長さ2のベクトル (`Array{SVector{2, T₂}}`) として2次元配列 `out₂` に格納されます。サブピクセル座標は、サブピクセルオフセットを整数成分に加えることで復元できます。

# 例

入力画像とアルゴリズムを `detect_subpixel_edges` に単純に渡すだけです。

```julia
f = Canny(spatial_scale = 1.4, thinning_algorithm = SubpixelNonmaximaSuppression())
img_edges, offsets = detect_subpixel_edges(img, f)
```

これは「アルゴリズム `f` を使用して画像 `img` の `detect_subpixel_edges`」と読み取れます。

戻り値の型を明示的に指定することもできます。

```julia
f = Canny(spatial_scale = 1.4, thinning_algorithm = SubpixelNonmaximaSuppression())
img_edges, offsets = detect_subpixel_edges(Gray{Float32}, Float32, img, f)
```

インプレースエッジ検出については [`detect_subpixel_edges!`](@ref) も参照してください。
