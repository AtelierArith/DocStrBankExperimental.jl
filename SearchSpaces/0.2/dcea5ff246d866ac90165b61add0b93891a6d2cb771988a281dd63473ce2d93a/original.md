```
BoxConstrainedSpace(;lb, ub, rigid=true)
```

Define a search space delimited by box constraints.

# Example

```julia-repl
julia> space = BoxConstrainedSpace(lb = zeros(Int, 5), ub = ones(Int, 5))
BoxConstrainedSpace{Int64}([0, 0, 0, 0, 0], [1, 1, 1, 1, 1], [1, 1, 1, 1, 1], 5, true)

julia> cardinality(space)
32
```
