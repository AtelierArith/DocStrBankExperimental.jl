```
constrained_triangulation(vertices::Array{Float64,2}, vertices_map::Array{Int64,1}, edges_list::Array{Int64,2}, edges_boundary::Array{Bool,1}, holes::Array{Float64,2})
```

`vertices`のリストに対して制約付きデローニ三角形分割を計算します。このリストは`[x1 y1; x2 y2; ... ; xn yn]`の形式です。また、保持されるエッジのリストも必要です。これらのエッジの一部はメッシュの境界としてマークできます。

`holes`のリストは、メッシュのその部分で三角形分割を避けるために、* [x1 y1; x2 y2; ... ; xn yn]*の形式で渡すことができます。

各頂点にカスタム整数識別子を持たせるために、`vertices_map`にインデックスのリストが提供されます。

最終的な三角形分割に含めるエッジのリストは、`edges_list`に`[ vertex-identifier-1 vertex-identifier-2; vertex-identifier-1 vertex-identifier-3; ... ; vertex-identifier-N vertex-identifier-M ]`の形式で渡されます。

境界マーカーのリストは、`edges_boundary`にブール値の形式で渡され、三角形分割器にエッジが境界上にあるかどうかを伝えます（インデックスは`edges_list`と同じです）。

この関数は、各三角形の定義において頂点識別子を使用して、3つの頂点のリストの配列を返します（正しい頂点の順序を持つ三角形）。

# 例

```jldoctest
julia> using Triangle

julia> points = Array{Float64,2}([0. 0.; 4. 0.; 2. 3.; 8. 0.; 6. 3.; 4. 6.])
6×2 Array{Float64,2}:
 0.0  0.0
 4.0  0.0
 2.0  3.0
 8.0  0.0
 6.0  3.0
 4.0  6.0

julia> points_map = [1, 2, 4, 3, 5, 6]
6-element Array{Int64,1}:
 1
 2
 4
 3
 5
 6

julia> edges_list = Array{Int64,2}([1 2; 2 3; 3 1; 2 4; 4 5; 5 2; 3 5; 5 6; 6 3])
9×2 Array{Int64,2}:
 1  2
 2  3
 3  1
 2  4
 4  5
 5  2
 3  5
 5  6
 6  3

julia> edge_boundary = [false,true,false,false,false,true,true,false,false]
9-element Array{Bool,1}:
 false
  true
 false
 false
 false
  true
  true
 false
 false

julia> holes = [4. 2.]
1×2 Array{Float64,2}:
 4.0  2.0

julia> Triangle.constrained_triangulation(points, points_map, edges_list, edge_boundary, holes)
3-element Array{Array{Int64,1},1}:
 [1,2,3]
 [5,6,3]
 [4,5,2]
```
