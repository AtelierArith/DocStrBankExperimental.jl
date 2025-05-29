```
rescale(L::ZZLat, r::RationalUnion) -> ZZLat
```

Return the lattice `L` in the quadratic space with form `r \Phi`.

# Examples

This can be useful to apply methods intended for positive definite lattices.

```jldoctest
julia> L = integer_lattice(gram=ZZ[-1 0; 0 -1])
Integer lattice of rank 2 and degree 2
with gram matrix
[-1    0]
[ 0   -1]

julia> shortest_vectors(rescale(L, -1))
2-element Vector{Vector{ZZRingElem}}:
 [0, 1]
 [1, 0]
```
