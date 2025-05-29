```
basic_triangulation_vertices(vertices::Array{Float64,2})
```

`[x1 y1; x2 y2; ... ; xn yn]` の形式で与えられた `vertices` のリストに対して、デローニ三角形分割を計算します。

この関数は、各三角形の定義における頂点座標を使用して、3つの頂点のリスト（正しい頂点の順序を持つ三角形）の配列を返します。

# 例

```jldoctest
julia> using Triangle

julia> points = Array{Float64,2}([0. 0.; 1. 0.; 0. 1.])
3×2 Array{Float64,2}:
 0.0  0.0
 1.0  0.0
 0.0  1.0

julia> Triangle.basic_triangulation_vertices(points)
1-element Array{Array{Float64,2},1}:
 [0.0 0.0; 1.0 0.0; 0.0 1.0]
```
