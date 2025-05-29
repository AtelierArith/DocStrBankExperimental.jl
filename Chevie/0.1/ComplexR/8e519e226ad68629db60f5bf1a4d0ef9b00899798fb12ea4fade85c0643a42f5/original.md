`codegrees(W::ComplexReflectionGroup)`

returns  the vector of codegrees of `W`  as a reflection group on the space `V`  of `reflrep(W)`.  These are  one less  than the  degrees of  the basic derivations of `W` on `SV⊗ V^vee`.

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> codegrees(W)
2-element Vector{Int64}:
 0
 2
```
