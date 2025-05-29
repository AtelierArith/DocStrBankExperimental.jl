`isparabolic(W)`

whether the reflection subgroup `W` is a parabolic subgroup of `parent(W)`.

```julia-repl
julia> W=complex_reflection_group(7)
G₇

julia> isparabolic(reflection_subgroup(W,[1,2]))
false

julia> isparabolic(reflection_subgroup(W,[1]))
true
```
