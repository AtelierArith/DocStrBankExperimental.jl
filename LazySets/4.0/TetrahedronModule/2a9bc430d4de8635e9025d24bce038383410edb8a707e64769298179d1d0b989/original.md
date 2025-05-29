```
Tetrahedron{N, VN<:AbstractVector{N}, VT<:AbstractVector{VN}} <: AbstractPolytope{N}
```

Type that represents a (3-dimensional) tetrahedron in vertex representation.

### Fields

  * `vertices` – list of vertices

### Examples

A tetrahedron can be constructed by passing the list of vertices. The following builds the tetrahedron with edge length 2 from the [wikipedia page Tetrahedron](https://en.wikipedia.org/wiki/Tetrahedron):

```jldoctest
julia> vertices = [[1, 0, -1/sqrt(2)], [-1, 0, -1/sqrt(2)], [0, 1, 1/sqrt(2)], [0, -1, 1/sqrt(2)]];

julia> T = Tetrahedron(vertices);

julia> dim(T)
3

julia> zeros(3) ∈ T
true

julia> σ(ones(3), T)
3-element Vector{Float64}:
 0.0
 1.0
 0.7071067811865475
```
