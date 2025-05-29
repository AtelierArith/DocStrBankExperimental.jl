```
add_graph_data!(dg::D, weight, attribute) where {D <: DataGraphUnion}
```

Add the value `weight` to the graph under the name attribute. If the attribute is already defined, the value will be reset to `weight`.
