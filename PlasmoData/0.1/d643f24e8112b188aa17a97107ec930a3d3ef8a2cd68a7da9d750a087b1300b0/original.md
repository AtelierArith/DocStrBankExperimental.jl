```
rename_node_attribute!(dg::D, attribute, new_name) where {D <: DataGraphUnion}
```

Rename the node data `attribute` as `new_name`. If `attribute` is not defined, returns an error.
