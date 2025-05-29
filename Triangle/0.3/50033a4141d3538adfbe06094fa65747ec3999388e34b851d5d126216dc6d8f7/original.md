```
constrained_triangulation(vertices::Array{Float64,2}, vertices_map::Array{Int64,1}, edges_list::Array{Int64,2}, edges_boundary::Array{Bool,1})
```

Compute a Constrained Delaunay triangulation for a list of `vertices` in the form of `[x1 y1; x2 y2; ... ; xn yn]` and a list of edges that will be kept. Some of those edges can be marked as the boundary of the mesh.

A list of indexes is provided in `vertices_map` so that each vertex can have a custom integer identifier.

A list of edge (to be included in the final triangulation) is passed in `edges_list` in the form of `[ vertex-identifier-1 vertex-identifier-2; vertex-identifier-1 vertex-identifier-3; ... ; vertex-identifier-N vertex-identifier-M ]`

A list of boundary markers passed in `edges_boundary` in the form of booleans that tell the triangulator if the edge is on the boundary or not (the indexing is the same of `edges_list`).

The function will return an array of array of 3-vertices lists (triangles with the correct vertices order) using the vertex identifiers in each triangle definition.

# Example

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
