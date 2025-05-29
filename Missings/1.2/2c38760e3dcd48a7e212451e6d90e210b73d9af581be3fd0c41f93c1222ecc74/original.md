```
emptymissing(f)
```

Return a function that takes at least one positional argument `x` and returns `missing` if `x` is empty (`isempty(x)` returns `true`) and otherwise returns `f(x, args...; kwargs...)`, where `args` are following positional arguments passed to `f` and `kwargs` are its keyword arguments.

# Examples

```
julia> emptymissing(last)([])
missing

julia> emptymissing(last)([1, 2, 3])
3

julia> emptymissing(first)([], 2)
missing

julia> emptymissing(first)([1], 2)
1-element Vector{Int64}:
1
```
