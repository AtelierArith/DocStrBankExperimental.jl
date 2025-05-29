```
vertex_property(g, name)
```

Return an vertex map corresponding to property `name` of vertices in `g`.

```
vertex_property(g)
```

Returns a dictionary with elements `property_name => vertex_map`.

```
vertex_property(g, v)
```

Returns a dictionary of the form `name => val` containing all the properties associated to vertex `v`.

```
vertex_property(g, v, name)
```

Equivalent to `vertex_property(g, v)[name]`.

[`vprop`](@ref) is the short form for this function.
