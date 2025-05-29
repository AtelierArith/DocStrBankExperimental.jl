```
ftuple(args...; kwargs...)
```

Construct a [`FrankenTuple`](@ref) from the given positional and keyword arguments.

# Examples

```jldoctest
julia> ftuple(1, 2)
FrankenTuple((1, 2), NamedTuple())

julia> ftuple(1, 2, a=3, b=4)
FrankenTuple((1, 2), (a = 3, b = 4))
```
