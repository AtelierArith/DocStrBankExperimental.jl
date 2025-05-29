```
constrained_triangulation(vertices::Array{Float64,2}, vertices_map::Array{Int64,1}, edges_list::Array{Int64,2}, edges_boundary::Array{Bool,1}, holes::Array{Float64,2})
```

Compute a Constrained Delaunay triangulation for a list of `vertices` in the form of `[x1 y1; x2 y2; ... ; xn yn]` and a list of edges that will be kept. Some of those edges can be marked as the boundary of the mesh.

A list of `holes` in the form of *[x1 y1; x2 y2; ... ; xn yn]* can be passed to avoid triangulation in that part of the mesh.

A list of indexes is provided in `vertices_map` so that each vertex can have a custom integer identifier.

A list of edge (to be included in the final triangulation) is passed in `edges_list` in the form of `[ vertex-identifier-1 vertex-identifier-2; vertex-identifier-1 vertex-identifier-3; ... ; vertex-identifier-N vertex-identifier-M ]`

A list of boundary markers passed in `edges_boundary` in the form of booleans that tell the triangulator if the edge is on the boundary or not (the indexing is the same of `edges_list`).

The function will return an array of array of 3-vertices lists (triangles with the correct vertices order) using the vertex identifiers in each triangle definition.

# Example

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
