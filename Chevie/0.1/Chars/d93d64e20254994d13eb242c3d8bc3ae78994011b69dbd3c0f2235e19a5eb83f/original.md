`representations(W)`

returns  the list  of representations  of the  complex reflection  group or Spets `W` (see `representation`).

```julia-repl
julia> representations(coxgroup(:B,2))
5-element Vector{Vector{Matrix{Int64}}}:
 [[1;;], [-1;;]]
 [[1 0; -1 -1], [1 2; 0 -1]]
 [[-1;;], [-1;;]]
 [[1;;], [1;;]]
 [[-1;;], [1;;]]
```
