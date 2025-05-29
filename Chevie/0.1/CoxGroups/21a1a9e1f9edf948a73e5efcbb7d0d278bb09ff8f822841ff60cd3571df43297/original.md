`standard_parabolic_class(W,I)`

`I`  should be a  subset of `eachindex(gens(W))`.  The function returns the list of such subsets `W`-conjugate to `I`.

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
