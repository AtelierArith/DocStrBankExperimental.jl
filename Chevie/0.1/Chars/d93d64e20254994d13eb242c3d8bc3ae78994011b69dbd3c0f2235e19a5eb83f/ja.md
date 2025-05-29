`representations(W)`

は、複素反射群またはスぺッツ `W` の表現のリストを返します（`representation` を参照）。

```julia-repl
julia> representations(coxgroup(:B,2))
5-element Vector{Vector{Matrix{Int64}}}:
 [[1;;], [-1;;]]
 [[1 0; -1 -1], [1 2; 0 -1]]
 [[-1;;], [-1;;]]
 [[1;;], [1;;]]
 [[-1;;], [1;;]]
```
