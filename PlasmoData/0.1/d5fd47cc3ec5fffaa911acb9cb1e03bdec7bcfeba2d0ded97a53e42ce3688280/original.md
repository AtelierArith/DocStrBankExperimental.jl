```
get_node_data(dg::D, attribute_list; nodes = dg.nodes) where {D <: DataGraphUnion}
```

Returns a matrix of the node data for the attributes in attribute list in the order that the attributes are defined in the list. If `nodes` is defined, returns the subset of data corresponding to `nodes` in the order that they are defined in `nodes`
