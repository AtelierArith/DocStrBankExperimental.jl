`abelian_invariants(G::Group )`

`G`  should be an abelian group. Such a group has a unique decomposition up to  isomorphism as a product of cyclic groups `C(n₁)×…×C(nₖ)` where `C(nᵢ)` is  a cyclic  group of  order `nᵢ`  and `nᵢ`  divides `nᵢ₊₁`.  The function returns the list `n₁,…,nₖ`.

```julia-repl
julia> abelian_invariants(Group(Perm(1,2),Perm(3,4,5),Perm(6,7)))
2-element Vector{Int64}:
 2
 6
```
