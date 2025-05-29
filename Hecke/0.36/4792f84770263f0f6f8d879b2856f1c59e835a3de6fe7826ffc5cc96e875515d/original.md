```
is_primitive(M::ZZLat, N::ZZLat) -> Bool
```

Given two $\mathbb Z$-lattices $N \subseteq M$, return whether `N` is a primitive sublattice of `M`.

# Examples

```jldoctest
julia> U = hyperbolic_plane_lattice(3);

julia> bU = basis_matrix(U);

julia> e1, e2 = bU[1:1,:], bU[2:2,:]
([1 0], [0 1])

julia> N = lattice_in_same_ambient_space(U, e1 + e2)
Integer lattice of rank 1 and degree 2
with gram matrix
[6]

julia> is_primitive(U, N)
true

julia> M = root_lattice(:A, 3);

julia> f = matrix(QQ, 3, 3, [0 1 1; -1 -1 -1; 1 1 0]);

julia> N = kernel_lattice(M, f+1)
Integer lattice of rank 1 and degree 3
with gram matrix
[4]

julia> is_primitive(M, N)
true
```
