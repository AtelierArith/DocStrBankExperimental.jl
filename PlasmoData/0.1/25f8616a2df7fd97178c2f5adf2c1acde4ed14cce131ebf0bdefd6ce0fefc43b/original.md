```
rename_edge_attribute!(dg::D, attribute, new_name) where {D <: DataGraphUnion}
```

Rename the edge data `attribute` as `new_name`. If `attribute` is not defined, returns an error.
