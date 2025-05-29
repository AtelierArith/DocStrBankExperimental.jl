```
add_edge_property!(g, name, T)
add_edge_property!(g, name, emap)
```

Add the edge property  `name` to `g`.

If a type `T` is given as an input, an edge map with valtype `T` is created and stored into `g`.

As an alternative, an existing edge map `emap` can be stored into `g`.

[`eprop!`](@ref) is the short form of this function.

**Example**

```julia
g = random_regular_graph(10, 3, Network)

add_edge_property!(g, "weight", Float64)
# or equivalently
eprop!(g, "weight", Float64)
```
