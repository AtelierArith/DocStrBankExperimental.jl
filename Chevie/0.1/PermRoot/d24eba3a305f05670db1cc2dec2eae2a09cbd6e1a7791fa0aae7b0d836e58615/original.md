`invariant_form(W::ComplexReflectionGroup)`

This  function  returns  the  matrix  `F`  (defined  up  to a scalar) of an Hermitian form invariant under the action of the reflection group `W`. That is, if `M` is the matrix of an element of `W`, then `M*F*M'=F`.

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> invariant_form(W)
2×2 Matrix{Int64}:
 1  0
 0  2
```
