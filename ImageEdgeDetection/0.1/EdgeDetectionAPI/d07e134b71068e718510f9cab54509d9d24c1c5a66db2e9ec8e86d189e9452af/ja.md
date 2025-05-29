```
thin_edges!([out,] mag, g₁, g₂, f::AbstractEdgeThinningAlgorithm, args...; kwargs...)
```

局所的な勾配方向に沿った勾配の大きさ `mag` の局所的な最大値を特定します。引数 `g₁` と `g₂` はそれぞれ、第一空間次元（y）および第二空間次元（x）における勾配を表します。

# 出力

`out` が指定されている場合、それはその場で変更されます。そうでない場合、`mag` がその場で変更されます。

# 例

単にアルゴリズムを `thin_edges!` に渡すだけです：

```julia
using TestImages, ImageFiltering
img =  Gray.(testimage("mandril"))

# 第一および第二空間次元における勾配
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# 勾配の大きさ
mag = hypot.(g₁, g₂)

f = SubpixelNonmaximaSuppression(threshold = Percentile(10))

thinned_edges = zeros(eltype(mag), axes(mag))
thin_edges!(thinned_edges, mag, g₁, g₂, f)
```

`mag` をその場で変更したい場合は、`thinned_edges` を手動で割り当てる必要はありません。便利なメソッドを使用してください：

```julia
thin_edges!(mag, g₁, g₂, f)
```

参照： [`thin_edges`](@ref) ```
