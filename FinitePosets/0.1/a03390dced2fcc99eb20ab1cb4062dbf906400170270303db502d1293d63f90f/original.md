`chainspoly(P)` the chain polynomial of the `Poset` or `CPoset`, returned as the list of its coefficients.

```julia-repl
julia> chainpoly(Poset(:powerset,3))
5-element Vector{Int64}:
  1
  8
 19
 18
  6
```
