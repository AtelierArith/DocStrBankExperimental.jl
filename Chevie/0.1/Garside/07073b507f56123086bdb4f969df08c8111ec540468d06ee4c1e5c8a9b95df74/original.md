`α(b::LocallyGarsideElt)`

returns as a Garside element  the first term in  the normal form of  `b` (`b[1]` returns this term as a simple).

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> b=BraidMonoid(W)(2,1,2,1,1)
121.1.1

julia> α(b)
121
```
