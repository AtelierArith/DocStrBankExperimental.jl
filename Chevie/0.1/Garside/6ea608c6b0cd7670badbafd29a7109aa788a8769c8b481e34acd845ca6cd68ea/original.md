`words(b::LocallyGarsideElt)`

returns all the decompositions in atoms of `b`

```julia-repl
julia> W=coxgroup(:A,2)
A₂

julia> pi=BraidMonoid(W)(longest(W))^2
Δ²

julia> words(pi)
8-element Vector{Vector{Int64}}:
 [1, 1, 2, 1, 1, 2]
 [1, 2, 1, 1, 2, 1]
 [1, 2, 1, 2, 1, 2]
 [1, 2, 2, 1, 2, 2]
 [2, 1, 1, 2, 1, 1]
 [2, 1, 2, 1, 2, 1]
 [2, 1, 2, 2, 1, 2]
 [2, 2, 1, 2, 2, 1]
```
