```
edge_property(g, name)
```

Return an edge map corresponding to property `name` of edges in `g`.

```
edge_property(g)
```

Returns a dictionary with elements `property_name => edge_map`.

```
edge_property(g, e)
edge_property(g, u, v)
```

Returns a dictionary of the form `name => val` containing all the properties associated to edge `e`.

```
edge_property(g, e, name)
edge_property(g, u, v, name)
```

Equivalent to `edge_property(g, e)[name]`

[`eprop`](@ref) is the short form of this function.
