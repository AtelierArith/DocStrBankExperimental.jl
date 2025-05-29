```
sc = simplicial_torus(p::Int)
```

Create a triangulation of the two-dimensional torus.

The function returns a simplicial complex which represents a two-dimensional torus. The argument `p` specifies the characteristic of the underlying field. This triangulation is taken from Figure 6.4 in Munkres' book on Algebraic Topology. The boundary vertices are labeled as letters as in the book, the five center vertices are labeled by `1` through `5`.

# Examples

```jldoctest
julia> println(homology(simplicial_torus(0)))
[1, 2, 1]

julia> println(homology(simplicial_torus(2)))
[1, 2, 1]

julia> println(homology(simplicial_torus(3)))
[1, 2, 1]
```
