```
rename_graph_attribute!(dg::D, attribute, new_name) where {D <: DataGraphUnion}
```

Rename the graph data `attribute` as `new_name`. If `attribute` is not defined, returns an error.
