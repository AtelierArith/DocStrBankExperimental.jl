`abelian_invariants(G::Group )`

`G` はアーベル群である必要があります。このような群は、同型に関して一意の分解を持ち、循環群の積 `C(n₁)×…×C(nₖ)` として表されます。ここで `C(nᵢ)` は順序 `nᵢ` の循環群であり、`nᵢ` は `nᵢ₊₁` を割り切ります。この関数はリスト `n₁,…,nₖ` を返します。

```julia-repl
julia> abelian_invariants(Group(Perm(1,2),Perm(3,4,5),Perm(6,7)))
2-element Vector{Int64}:
 2
 6
```
