```
basic_triangulation(vertices::Array{Float64,2},vertices_map::Array{Int64,1})
```

`[x1 y1; x2 y2; ... ; xn yn]` の形式で与えられた `vertices` のリストに対して Delaunay 三角形分割を計算します。

各頂点にカスタム整数識別子を持たせるために、`vertices_map` にインデックスのリストが提供されます。

この関数は、各三角形の定義において頂点識別子を使用した 3 頂点リストの配列の配列を返します。

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

julia> Triangle.basic_triangulation(points,points_map)
1-element Array{Array{Int64,1},1}:
 [1, 2, 3]
```
