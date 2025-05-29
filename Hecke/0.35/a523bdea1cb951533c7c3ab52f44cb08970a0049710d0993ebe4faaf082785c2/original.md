```
irreducible_components(L::ZZLat) -> Vector{ZZLat}
```

Return the irreducible components $L_i$ of the definite lattice $L$.

This yields a maximal orthogonal splitting of `L` as

$$
L = \bigoplus_i L_i.
$$

The decomposition is unique up to ordering of the factors.

# Examples

```jldoctest
julia> R = integer_lattice(; gram=2 * identity_matrix(ZZ, 24));

julia> N = maximal_even_lattice(R); # Niemeier lattice

julia> irr_comp = irreducible_components(N)
3-element Vector{ZZLat}:
 Integer lattice of rank 8 and degree 24
 Integer lattice of rank 8 and degree 24
 Integer lattice of rank 8 and degree 24

julia> genus.(irr_comp)
3-element Vector{ZZGenus}:
 Genus symbol: II_(8, 0)
 Genus symbol: II_(8, 0)
 Genus symbol: II_(8, 0)
```
