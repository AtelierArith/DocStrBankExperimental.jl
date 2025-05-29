`endomorphisms(C::Category,o)` returns generators of the endomorphisms of `C.obj[o]`

```julia-repl
julia> W=coxsym(4);M=BraidMonoid(W)
BraidMonoid(𝔖 ₄)

julia> endomorphisms(conjcat(M(1,1,2,2,3)),1)
2-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, CoxSym{Int16}}}}:
 213.1232
 12.213
```
