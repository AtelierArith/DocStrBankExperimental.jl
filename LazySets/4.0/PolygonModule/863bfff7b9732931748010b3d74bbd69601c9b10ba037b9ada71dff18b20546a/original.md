```
Polygon{N, VN<:AbstractVector{N}} <: LazySet{N}
```

Type that represents a non-convex polygon by its vertices.

### Fields

  * `vertices` – the list of vertices (in clockwise or counter-clockwise order)

### Examples

A non-convex polygon in vertex representation can be constructed by passing the list of vertices. For example, we can build a tooth:

```jldoctest polygon_v_ncrep
julia> P = Polygon([[0.0, 0], [0, 2], [2, 2], [2, 0], [1, 1]]);

julia> P.vertices
5-element Vector{Vector{Float64}}:
 [0.0, 0.0]
 [0.0, 2.0]
 [2.0, 2.0]
 [2.0, 0.0]
 [1.0, 1.0]
```
