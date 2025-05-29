`endomorphisms(C::Category,o)` は `C.obj[o]` の自己準同型の生成子を返します。

```julia-repl
julia> W=coxsym(4);M=BraidMonoid(W)
BraidMonoid(𝔖 ₄)

julia> endomorphisms(conjcat(M(1,1,2,2,3)),1)
2-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, CoxSym{Int16}}}}:
 213.1232
 12.213
```
