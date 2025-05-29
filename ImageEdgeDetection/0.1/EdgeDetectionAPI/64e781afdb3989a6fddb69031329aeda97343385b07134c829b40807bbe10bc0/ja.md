```
out₁, out₂ = thin_subpixel_edges(mag, g₁, g₂, f::AbstractEdgeThinningAlgorithm, args...; kwargs...)
```

局所勾配方向に沿った勾配大きさ `mag` の局所最大値を特定します。引数 `g₁` と `g₂` はそれぞれ、第一空間次元（y）および第二空間次元（x）における勾配を表します。

# 出力

局所最大値の整数成分は、`out₁` の非ゼロ行および列のエントリに対応します。付随するサブピクセルオフセットは、長さ2のベクトルとして2次元配列 `out₂` に格納されます。サブピクセル座標は、サブピクセルオフセットを整数成分に加えることで復元できます。

# 例

アルゴリズムを `thin_subpixel_edges` に単純に渡します：

```julia
using TestImages, ImageFiltering
img =  Gray.(testimage("mandril"))

# 第一および第二空間次元における勾配
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# 勾配大きさ
mag = hypot.(g₁, g₂)

f = SubpixelNonmaximaSuppression(threshold = Percentile(10))

thinned_edges, offsets = thin_subpixel_edges(mag, g₁, g₂, f)
```

参照： [`thin_subpixel_edges!`](@ref)
