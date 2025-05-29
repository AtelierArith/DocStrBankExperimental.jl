```
add_node_data!(dg::D, node_name, node_weight, attribute_name) where {D <: DataGraphUnion}
```

Add a weight value for the given node name in the DataGraph object. User must pass an "attribute name" for the given weight. All other nodes that do not have a node_weight value defined for that attribute name default to a value of zero.
