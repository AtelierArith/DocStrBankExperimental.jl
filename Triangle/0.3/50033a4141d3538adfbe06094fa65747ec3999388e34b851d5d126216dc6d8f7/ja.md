```
constrained_triangulation(vertices::Array{Float64,2}, vertices_map::Array{Int64,1}, edges_list::Array{Int64,2}, edges_boundary::Array{Bool,1})
```

`vertices`のリストに対して制約付きデローニ三角形分割を計算します。`vertices`は`[x1 y1; x2 y2; ... ; xn yn]`の形式で、保持されるエッジのリストがあります。これらのエッジの一部はメッシュの境界としてマークされることがあります。

各頂点にカスタム整数識別子を持たせるために、`vertices_map`にインデックスのリストが提供されます。

最終的な三角形分割に含めるエッジのリストは、`edges_list`に`[ vertex-identifier-1 vertex-identifier-2; vertex-identifier-1 vertex-identifier-3; ... ; vertex-identifier-N vertex-identifier-M ]`の形式で渡されます。

境界マーカーのリストは、`edges_boundary`にブール値の形式で渡され、三角形分割器にエッジが境界上にあるかどうかを伝えます（インデックスは`edges_list`と同じです）。

この関数は、各三角形の定義において頂点識別子を使用した3頂点リストの配列を返します。

# 例

```jldoctest
julia> using Triangle

julia> points = [0. 0.; 0. 3.; 1. 3.; 1. 1.; 2. 1.; 2. 0.]
6×2 Array{Float64,2}:
 0.0  0.0
 0.0  3.0
 1.0  3.0
 1.0  1.0
 2.0  1.0
 2.0  0.0

julia> points_map = Array{Int64,1}(collect(1:1:size(points)[1]))
6-element Array{Int64,1}:
 1
 2
 3
 4
 5
 6

julia> edges_list = Array{Int64,2}([1 2; 2 3; 3 4; 4 5; 5 6; 6 1])
6×2 Array{Int64,2}:
 1  2
 2  3
 3  4
 4  5
 5  6
 6  1

julia> edge_boundary = [false, false, true, true, false, false]
6-element Array{Bool,1}:
 false
 false
  true
  true
 false
 false

julia> Triangle.constrained_triangulation(points,points_map,edges_list,edge_boundary)
4-element Array{Array{Int64,1},1}:
 [1, 4, 2]
 [4, 1, 6]
 [2, 4, 3]
 [5, 4, 6]
```
