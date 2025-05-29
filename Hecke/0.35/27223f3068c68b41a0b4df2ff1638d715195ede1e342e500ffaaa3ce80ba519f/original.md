```
root_sublattice(L::ZZLat) -> ZZLat
```

Return the sublattice spanned by the roots of length at most $2$.

Input:

`L` - a definite integral lattice

Output:

The sublattice of `L` spanned by all vectors `x` of `L` with $|x^2|\leq 2$.

# Examples

```jldoctest
julia> L = integer_lattice(gram = ZZ[2 0; 0 4]);

julia> root_sublattice(L)
Integer lattice of rank 1 and degree 2
with gram matrix
[2]

julia> basis_matrix(root_sublattice(L))
[1   0]
```
