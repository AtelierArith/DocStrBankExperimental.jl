```
basic_triangulation_vertices(vertices::Array{Float64,2},vertices_map::Array{Int64,1})
```

`vertices`のリストに対してDelaunay三角形分割を計算します。このリストは`[x1 y1; x2 y2; ... ; xn yn]`の形式です。

各頂点にカスタム整数識別子を持たせるために、`vertices_map`にインデックスのリストが提供されます。

この関数は、各三角形の定義における頂点座標を使用して、3つの頂点のリストの配列（正しい頂点の順序を持つ三角形）を返します。

# 例

```jldoctest
julia> using Triangle 

julia> points = Array{Float64,2}([0. 0.; 1. 0.; 0. 1.])
3×2 Array{Float64,2}:
 0.0  0.0
 1.0  0.0
 0.0  1.0

julia> points_map = [1, 2, 3]
3-element Array{Int64,1}:
 1
 2
 3

julia> Triangle.basic_triangulation_vertices(points,points_map)
1-element Array{Array{Float64,2},1}:
 [0.0 0.0; 1.0 0.0; 0.0 1.0]
```
