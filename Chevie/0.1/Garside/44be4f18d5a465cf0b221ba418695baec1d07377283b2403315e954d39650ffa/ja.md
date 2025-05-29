`α(b::LocallyGarsideElt,I)`

は `b.M.atoms[I]` のみを使用して b の最長接頭辞を返します。

```julia-repl
julia> W=coxgroup(:A,4);B=BraidMonoid(W)
BraidMonoid(A₄)

julia> w0=B(longest(W))
Δ

julia> α(w0,[1,2,3])
121321
```
