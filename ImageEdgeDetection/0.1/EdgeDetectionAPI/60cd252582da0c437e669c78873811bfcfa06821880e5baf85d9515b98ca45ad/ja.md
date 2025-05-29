```
detect_subpixel_edges!(out₁, out₂, img, f::AbstractEdgeDetectionAlgorithm, args...; kwargs...)
```

画像 `img` のエッジをサブピクセル精度で検出するためにアルゴリズム `f` を使用します。指定されていない場合、`f` は [`Canny`](@ref ImageEdgeDetection.Canny) であると見なされます。

# 出力

エッジの整数成分は `out₁` の非ゼロ行および列のエントリに対応します。対応するサブピクセルオフセットは、長さ2のベクトルとして2次元配列 `out₂` に格納されます。サブピクセル座標は、サブピクセルオフセットを整数成分に加えることで回復できます。

# 例

アルゴリズムを `detect_subpixel_edges!` に単純に渡すだけです：

```julia
f = Canny(spatial_scale = 1.4, thinning_algorithm = SubpixelNonmaximaSuppression())
img_edges = similar(img)
offsets = zeros(SVector{2,Float64}, axes(img))
detect_edges!(img_edges, offsets, img, f)
```

参照： [`detect_subpixel_edges`](@ref) ```
