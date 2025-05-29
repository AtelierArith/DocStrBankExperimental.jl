`α(b::LocallyGarsideElt)`

は、`b` の正規形の最初の項を Garside 要素として返します（`b[1]` はこの項を単純なものとして返します）。

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> b=BraidMonoid(W)(2,1,2,1,1)
121.1.1

julia> α(b)
121
```
