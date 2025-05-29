```
sc = simplicial_projective_plane(p::Int)
```

Create a triangulation of the projective plane.

The function returns a simplicial complex which represents the projective plane. The argument `p` specifies the characteristic of the underlying field. This triangulation is taken from Figure 6.6 in Munkres' book on Algebraic Topology. The boundary vertices are labeled as letters as in the book, the five center vertices are labeled by `1` through `5`.

# Examples

```jldoctest
julia> println(homology(simplicial_projective_plane(0)))
[1, 0, 0]

julia> println(homology(simplicial_projective_plane(2)))
[1, 1, 1]

julia> println(homology(simplicial_projective_plane(3)))
[1, 0, 0]
```
