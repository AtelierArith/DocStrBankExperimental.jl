```
basic_triangulation_vertices(vertices::Array{Float64,2})
```

Compute a Delaunay triangulation for a list of `vertices` in the form of `[x1 y1; x2 y2; ... ; xn yn]`

The function will return an array of array of 3-vertices lists (triangles with the correct vertices order) using the vertex coordinates in each triangle definition.

# Example

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
