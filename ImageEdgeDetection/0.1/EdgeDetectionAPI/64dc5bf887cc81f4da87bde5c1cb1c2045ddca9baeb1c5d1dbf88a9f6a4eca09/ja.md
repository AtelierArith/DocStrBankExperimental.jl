```
thin_subpixel_edges!(out₁, out₂, mag, g₁, g₂, f::AbstractEdgeThinningAlgorithm, args...; kwargs...)
```

局所勾配方向に沿った勾配大きさ `mag` の局所最大値を特定します。引数 `g₁` と `g₂` はそれぞれ、最初の空間次元（y）および第二の空間次元（x）における勾配を表します。

# 出力

局所最大値の整数成分は、`out₁` の非ゼロ行および列のエントリに対応します。付随するサブピクセルオフセットは、長さ2のベクトルとして2次元配列 `out₂` に格納されます。サブピクセル座標は、サブピクセルオフセットを整数成分に加えることで回復できます。

# 例

アルゴリズムを `thin_subpixel_edges!` に単純に渡します：

```julia
using TestImages, ImageFiltering
img =  Gray.(testimage("mandril"))

# 最初と第二の空間次元における勾配
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# 勾配の大きさ
mag = hypot.(g₁, g₂)

f = SubpixelNonmaximaSuppression(threshold = Percentile(10))

thinned_edges = zeros(eltype(mag), axes(mag))
offsets = zeros(SVector{2,Float64}, axes(mag))
thin_subpixel_edges!(thinned_edges, offsets, mag, g₁, g₂, f)
```

参照： [`thin_subpixel_edges`](@ref)
