`reflection_character(W::ComplexReflectionGroup,w)` or `reflchar`

Returns  the trace  of the  element `w`  of `W`  as an  endomorphism of the vector space `V` on which `W` acts.

```julia-repl
julia> W=coxgroup(:B,3)
B₃

julia> reflchar(W,longest(W))
-3
```
