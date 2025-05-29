```
leech_lattice(niemeier_lattice::ZZLat) -> ZZLat, QQMatrix, Int
```

Return a triple `L, v, h` where `L` is the Leech lattice.

L is an `h`-neighbor of the Niemeier lattice `N` with respect to `v`. This means that `L / L ∩ N  ≅ ℤ / h ℤ`. Here `h` is the Coxeter number of the Niemeier lattice.

This implements the 23 holy constructions of the Leech lattice in [CS99](@cite).

# Examples

```jldoctest leech
julia> R = integer_lattice(gram=2 * identity_matrix(ZZ, 24));

julia> N = maximal_even_lattice(R) # Some Niemeier lattice
Integer lattice of rank 24 and degree 24
with gram matrix
[2   1   1   1   0   0   0   0   0   0   0   0   0   0   0   0   1   0   1   1   0   0   0   0]
[1   2   1   1   0   0   0   0   0   0   0   0   0   0   0   0   1   1   0   1   0   0   0   0]
[1   1   2   1   0   0   0   0   0   0   0   0   0   0   0   0   1   1   1   0   0   0   0   0]
[1   1   1   2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
[0   0   0   0   2   1   1   1   0   0   0   0   1   0   1   1   0   0   0   0   0   0   0   0]
[0   0   0   0   1   2   1   1   0   0   0   0   1   1   0   1   0   0   0   0   0   0   0   0]
[0   0   0   0   1   1   2   1   0   0   0   0   1   1   1   0   0   0   0   0   0   0   0   0]
[0   0   0   0   1   1   1   2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0]
[0   0   0   0   0   0   0   0   2   1   1   1   0   0   0   0   0   0   0   0   1   1   1   0]
[0   0   0   0   0   0   0   0   1   2   1   1   0   0   0   0   0   0   0   0   1   0   1   1]
[0   0   0   0   0   0   0   0   1   1   2   1   0   0   0   0   0   0   0   0   1   1   0   1]
[0   0   0   0   0   0   0   0   1   1   1   2   0   0   0   0   0   0   0   0   0   0   0   0]
[0   0   0   0   1   1   1   0   0   0   0   0   2   1   1   1   0   0   0   0   0   0   0   0]
[0   0   0   0   0   1   1   0   0   0   0   0   1   2   0   0   0   0   0   0   0   0   0   0]
[0   0   0   0   1   0   1   0   0   0   0   0   1   0   2   0   0   0   0   0   0   0   0   0]
[0   0   0   0   1   1   0   0   0   0   0   0   1   0   0   2   0   0   0   0   0   0   0   0]
[1   1   1   0   0   0   0   0   0   0   0   0   0   0   0   0   2   1   1   1   0   0   0   0]
[0   1   1   0   0   0   0   0   0   0   0   0   0   0   0   0   1   2   0   0   0   0   0   0]
[1   0   1   0   0   0   0   0   0   0   0   0   0   0   0   0   1   0   2   0   0   0   0   0]
[1   1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   1   0   0   2   0   0   0   0]
[0   0   0   0   0   0   0   0   1   1   1   0   0   0   0   0   0   0   0   0   2   1   1   1]
[0   0   0   0   0   0   0   0   1   0   1   0   0   0   0   0   0   0   0   0   1   2   0   0]
[0   0   0   0   0   0   0   0   1   1   0   0   0   0   0   0   0   0   0   0   1   0   2   0]
[0   0   0   0   0   0   0   0   0   1   1   0   0   0   0   0   0   0   0   0   1   0   0   2]

julia> minimum(N)
2

julia> det(N)
1

julia> L, v, h = leech_lattice(N);

julia> minimum(L)
4

julia> det(L)
1

julia> h == index(L, intersect(L, N))
true

```

We illustrate how the Leech lattice is constructed from `N`, `h` and `v`.

```jldoctest leech
julia> Zmodh, _ = residue_ring(ZZ, h);

julia> V = ambient_space(N);

julia> vG = map_entries(x->Zmodh(ZZ(x)), inner_product(V, v, basis_matrix(N)));

julia> LN = transpose(lift(Hecke.kernel(vG; side = :right)))*basis_matrix(N); # vectors whose inner product with `v` is divisible by `h`.

julia> M = lattice(V, LN) + h*N;

julia> M == intersect(L, N)
true

julia> M + lattice(V, 1//h * v) == L
true

```
