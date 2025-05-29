```
set_graph_property!(g, name, x)
```

Set the property `name` to value `x` to `g`. Creates the property if it doesn't exist. [`gprop!`](@ref) can be conveniently used as a short form of this function.

**Example**

```julia
g = Network(10, 20)
set_graph_property!(g, "label", "My Network")
# or equivalently
gprop!(g, "label", "My Network")
```
