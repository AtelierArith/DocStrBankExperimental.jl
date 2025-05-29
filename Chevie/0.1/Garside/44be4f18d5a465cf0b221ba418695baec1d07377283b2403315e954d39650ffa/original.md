`α(b::LocallyGarsideElt,I)`

returns the longest prefix of b using only `b.M.atoms[I]`

```julia-repl
julia> W=coxgroup(:A,4);B=BraidMonoid(W)
BraidMonoid(A₄)

julia> w0=B(longest(W))
Δ

julia> α(w0,[1,2,3])
121321
```
