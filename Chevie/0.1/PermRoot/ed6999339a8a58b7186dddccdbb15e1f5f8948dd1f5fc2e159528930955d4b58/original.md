`reflection_character(W::ComplexReflectionGroup)` or `reflchar`

Returns  the reflection  character of  `W`. When  `W` is irreducible, it is `CharTable(W).irr[charinfo(W).extRefl[2]]`.

```julia-repl
julia> reflchar(coxgroup(:A,3))
5-element Vector{Int64}:
  3
  1
 -1
  0
 -1
```
