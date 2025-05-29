```
even_sublattice(L::ZZLat) -> ZZLat
```

Given an integral $\mathbb{Z}$-lattice `L`, i.e. such that the bilinear form on `L` is integral, return the largest even sublattice `L0` of `L`.

If `L` is already even, then $L0 = L$.

# Examples

```jldoctest
julia> L = integer_lattice(; gram=QQ[3 0; 0 16])
Integer lattice of rank 2 and degree 2
with gram matrix
[3    0]
[0   16]

julia> L0 = even_sublattice(L)
Integer lattice of rank 2 and degree 2
with gram matrix
[12    0]
[ 0   16]

julia> index(L, L0)
2
```
