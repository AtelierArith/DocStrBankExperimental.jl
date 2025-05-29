`parabolic_closure(W,I)`

`I`  should be a  list of indices  of reflections of  `W`. Returns `J` such that  `reflection_subgroup(W,J)` is the smallest  parabolic subgroup of `W` containing `reflection_subgroup(W,I)`.

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
