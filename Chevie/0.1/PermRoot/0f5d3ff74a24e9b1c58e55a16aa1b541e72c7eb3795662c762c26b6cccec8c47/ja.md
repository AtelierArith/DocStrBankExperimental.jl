`isparabolic(W)`

反射部分群 `W` が `parent(W)` の放物部分群であるかどうかを判定します。

```julia-repl
julia> W=complex_reflection_group(7)
G₇

julia> isparabolic(reflection_subgroup(W,[1,2]))
false

julia> isparabolic(reflection_subgroup(W,[1]))
true
```
