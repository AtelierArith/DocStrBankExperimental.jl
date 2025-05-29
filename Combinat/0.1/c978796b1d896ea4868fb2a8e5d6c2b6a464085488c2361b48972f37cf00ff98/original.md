`groupby(f::Function,l)`

group  elements of collection `l` according to the values taken by function `f` on them. The values of `f` must be hashable.

```julia-repl
julia> groupby(iseven,1:10)
Dict{Bool, Vector{Int64}} with 2 entries:
  0 => [1, 3, 5, 7, 9]
  1 => [2, 4, 6, 8, 10]
```

Note:  keys of the result will  have type `Any` if `l`  is empty since I do not know how to access the return type of a function
