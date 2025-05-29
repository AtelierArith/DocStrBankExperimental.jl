```
VPolygon{N, VN<:AbstractVector{N}} <: AbstractPolygon{N}
```

Type that represents a polygon by its vertices.

### Fields

  * `vertices` – the list of vertices

### Notes

This type assumes that all vertices are sorted in counter-clockwise fashion.

To ensure this property, the constructor of `VPolygon` runs a convex-hull algorithm on the vertices by default. This also removes redundant vertices. If the vertices are known to be sorted, the flag `apply_convex_hull=false` can be used to skip this preprocessing.

### Examples

A polygon in vertex representation can be constructed by passing the list of vertices. For example, we can build the right triangle

```jldoctest polygon_vrep
julia> P = VPolygon([[0, 0], [1, 0], [0, 1]]);

julia> P.vertices
3-element Vector{Vector{Int64}}:
 [0, 0]
 [1, 0]
 [0, 1]
```

Alternatively, a `VPolygon` can be constructed passing a matrix of vertices, where each *column* represents a vertex:

```jldoctest polygon_vrep
julia> M = [0 1 0; 0 0 1.]
2×3 Matrix{Float64}:
 0.0  1.0  0.0
 0.0  0.0  1.0

julia> P = VPolygon(M);

julia> P.vertices
3-element Vector{Vector{Float64}}:
 [0.0, 0.0]
 [1.0, 0.0]
 [0.0, 1.0]
```
