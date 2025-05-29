```
sylow_subgroup(G::FinGenAbGroup, p::IntegerUnion) -> FinGenAbGroup, FinGenAbGroupHom
```

Return the Sylow $p-$subgroup of the finitely generated abelian group `G`, for a prime `p`. This is the subgroup of `p`-power order in `G` whose index in `G` is coprime to `p`.

# Examples

```jldoctest
julia> A = abelian_group(ZZRingElem[2, 6, 30])
Z/2 x Z/6 x Z/30

julia> H, j = sylow_subgroup(A, 2);

julia> H
(Z/2)^3

julia> divexact(order(A), order(H))
45
```
