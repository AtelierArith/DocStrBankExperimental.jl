`parabolic_closure(W,I)`

`I` は `W` の反射のインデックスのリストである必要があります。`reflection_subgroup(W,J)` が `reflection_subgroup(W,I)` を含む `W` の最小の放物群を返します。

```julia-repl
julia> W=complex_reflection_group(7)
G₇

julia> parabolic_closure(W,[1])
1-element Vector{Int64}:
 1

julia> parabolic_closure(W,[1,2])
3-element Vector{Int64}:
 1
 2
 3
```
