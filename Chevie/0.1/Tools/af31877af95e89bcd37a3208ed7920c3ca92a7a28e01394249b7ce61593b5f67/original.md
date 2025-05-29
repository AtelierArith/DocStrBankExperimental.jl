`abelian_gens(A)`

`A`  should be an abelian group or the list of its generators. Such a group has  a unique decomposition up to isomorphism as a product of cyclic groups `C(n₁)×…×C(nₖ)`  where `C(nᵢ)`  is a  cyclic group  of order  `nᵢ` and `nᵢ` divides  `nᵢ₊₁`. The function returns a list  of generators for each of the `C(nᵢ)`.

```julia-repl
julia> abelian_gens([Perm(1,2),Perm(3,4,5),Perm(6,7)])
2-element Vector{Perm{Int16}}:
 (6,7)
 (1,2)(3,5,4)(6,7)
```
