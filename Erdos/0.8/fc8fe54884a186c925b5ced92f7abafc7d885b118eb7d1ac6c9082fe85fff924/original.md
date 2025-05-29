```
add_vertex_property!(g, name, T)
add_vertex_property!(g, name, vmap)
```

Add the vertex property  `name` to `g`.

If a type `T` is given as an input, a vertex map with valtype `T` is created and stored into `g`.

As an alternative, an existing vertex map `vmap` can be stored into `g`.

[`vprop!`](@ref) is the short form of this function.
