```
draw!(img::AbstractArray{T,2}, verts::Vector{CartesianIndex{2}}, f::AbstractPolyFillAlgorithm; closed::Bool)
```

`img`にアルゴリズム`f`を使用して描画します。

# 出力

`img`が指定されると、`img`に変更が加えられ、返されます。

# 例

アルゴリズムをパラメータとともに、画像と多角形の頂点を渡すだけです。

```julia
using ImageDraw

img = zeros(RGB, 7, 7)
expected = copy(img)
expected[2:6, 2:6] .= RGB{N0f8}(1)

verts = [CartesianIndex(2, 2), CartesianIndex(2, 6), CartesianIndex(6, 6), CartesianIndex(6, 2), CartesianIndex(2,2)]

draw!(img, verts, BoundaryFill(4, 4; fill_value = RGB(1), boundary_value = RGB(1)); closed = true)
```
