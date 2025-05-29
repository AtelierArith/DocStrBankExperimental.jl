```
primitive_closure(M::ZZLat, N::ZZLat) -> ZZLat
```

Given two $\mathbb Z$-lattices `M` and `N` with $N \subseteq \mathbb{Q} M$, return the primitive closure $M \cap \mathbb{Q} N$ of `N` in `M`.

# Examples

```jldoctest
julia> M = root_lattice(:D, 6);

julia> N = lattice_in_same_ambient_space(M, 3*basis_matrix(M)[1:1,:]);

julia> basis_matrix(N)
[3   0   0   0   0   0]

julia> N2 = primitive_closure(M, N)
Integer lattice of rank 1 and degree 6
with gram matrix
[2]

julia> basis_matrix(N2)
[1   0   0   0   0   0]

julia> M2 = primitive_closure(dual(M), M);

julia> is_integral(M2)
false

```
