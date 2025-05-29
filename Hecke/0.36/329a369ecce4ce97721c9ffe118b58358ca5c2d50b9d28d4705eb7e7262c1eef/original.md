```
gram_matrix(L::ZZLat) -> QQMatrix
```

Return the gram matrix of $L$.

# Examples

```jldoctest
julia> L = integer_lattice(matrix(ZZ, [2 0; -1 2]));

julia> gram_matrix(L)
[ 4   -2]
[-2    5]
```
