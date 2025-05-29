```
@enumx
```

Macro for generating an enum type with instances.

`@enumx` can be used as a drop in replacement for `@enum` from `Base`, but have several improvements. See the [README](https://github.com/fredrikekre/EnumX.jl) or the module docstring (`?EnumX` in the REPL) for more details.

# Examples

```julia
julia> @enumx Fruit Apple Banana

julia> Fruit.T
Enum type Fruit.T <: Enum{Int32} with 2 instances:
 Fruit.Apple  = 0
 Fruit.Banana = 1

julia> Fruit.Apple
Fruit.Apple = 0
```
