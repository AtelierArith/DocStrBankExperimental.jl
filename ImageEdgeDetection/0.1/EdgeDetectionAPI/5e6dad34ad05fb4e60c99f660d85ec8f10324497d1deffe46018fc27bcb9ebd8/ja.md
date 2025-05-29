```
thin_edges([T::Type,] mag, g₁, g₂, f::AbstractEdgeThinningAlgorithm, args...; kwargs...)
```

アルゴリズム `f` を使用して、エッジの大きさ `mag`、第一空間次元の勾配 `g₁`、および第二空間次元の勾配 `g₂` に基づいてエッジ応答を細くします。

# 出力

細くされたエッジ応答を表す `Array{T}` を返します。

`T` が指定されていない場合は、推測されます。`T` は浮動小数点数を表すか、ラップする必要があります。

# 例

入力画像とアルゴリズムを `thin_edges` に単純に渡します。

```julia
using TestImages, ImageFiltering
img =  Gray.(testimage("mandril"))

# 第一および第二空間次元の勾配
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# 勾配の大きさ
mag = hypot.(g₁, g₂)

f = NonmaximaSuppression(threshold = Percentile(10))

thinned_edges = thin_edges(mag, g₁, g₂, f)
```

これは「エッジ応答の大きさと空間勾配に基づいて、アルゴリズム `f` を使用して `thin_edges` を実行する」と読み取れます。

戻り値の型を明示的に指定することもできます：

```julia
thinned_edges_float32 = thin_edges(Gray{Float32}, mag, g₁, g₂, f)
```

インプレースのエッジ細化については [`thin_edges!`](@ref) を参照してください。
