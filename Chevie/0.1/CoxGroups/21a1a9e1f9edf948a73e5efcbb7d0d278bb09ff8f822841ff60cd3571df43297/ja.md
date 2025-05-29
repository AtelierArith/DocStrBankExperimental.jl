`standard_parabolic_class(W,I)`

`I` は `eachindex(gens(W))` の部分集合である必要があります。この関数は、`I` に対して `W`-共役なそのような部分集合のリストを返します。

```julia-repl
julia> CoxGroups.standard_parabolic_class(coxgroup(:E,8),[7,8])
7-element Vector{Vector{Int64}}:
 [7, 8]
 [6, 7]
 [5, 6]
 [4, 5]
 [2, 4]
 [3, 4]
 [1, 3]
```
