```
rational_span(L::ZZLat) -> QuadSpace
```

Return the rational span of $L$, which is the quadratic space with Gram matrix equal to `gram_matrix(L)`.

# Examples

```jldoctest
julia> L = integer_lattice(matrix(ZZ, [2 0; -1 2]));

julia> rational_span(L)
Quadratic space of dimension 2
  over rational field
with gram matrix
[ 4   -2]
[-2    5]
```
