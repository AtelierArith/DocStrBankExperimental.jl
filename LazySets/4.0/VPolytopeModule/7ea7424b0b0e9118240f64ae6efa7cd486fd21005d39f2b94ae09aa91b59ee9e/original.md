```
VPolytope{N, VN<:AbstractVector{N}, VT<:AbstractVector{VN}} <: AbstractPolytope{N}
```

Type that represents a convex polytope in vertex representation.

### Fields

  * `vertices` – list of vertices

### Examples

A polytope in vertex representation can be constructed by passing the list of vertices. For example, we can build the tetrahedron:

```jldoctest
julia> P = VPolytope([[0, 0, 0], [1, 0, 0], [0, 1, 0], [0, 0, 1]]);

julia> P.vertices
4-element Vector{Vector{Int64}}:
 [0, 0, 0]
 [1, 0, 0]
 [0, 1, 0]
 [0, 0, 1]
```

Alternatively, a `VPolytope` can be constructed passing a matrix of vertices, where each *column* represents a vertex:

```jldoctest
julia> M = [0 0 0; 1 0 0; 0 1 0; 0 0 1]'
3×4 adjoint(::Matrix{Int64}) with eltype Int64:
 0  1  0  0
 0  0  1  0
 0  0  0  1

julia> P = VPolytope(M);

julia> P.vertices
4-element Vector{Vector{Int64}}:
 [0, 0, 0]
 [1, 0, 0]
 [0, 1, 0]
 [0, 0, 1]
```
