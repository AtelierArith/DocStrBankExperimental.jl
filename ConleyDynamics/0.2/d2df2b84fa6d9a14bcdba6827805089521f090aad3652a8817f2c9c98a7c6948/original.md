```
sc = simplicial_klein_bottle(p::Int)
```

Create a triangulation of the two-dimensional Klein bottle.

The function returns a simplicial complex which represents the two-dimensional Klein bottle. The argument `p` specifies the characteristic of the underlying field. This triangulation is taken from Figure 6.6 in Munkres' book on Algebraic Topology. The boundary vertices are labeled as letters as in the book, the five center vertices are labeled by `1` through `5`.

# Examples

```jldoctest
julia> println(homology(simplicial_klein_bottle(0)))
[1, 1, 0]

julia> println(homology(simplicial_klein_bottle(2)))
[1, 2, 1]

julia> println(homology(simplicial_klein_bottle(3)))
[1, 1, 0]
```
