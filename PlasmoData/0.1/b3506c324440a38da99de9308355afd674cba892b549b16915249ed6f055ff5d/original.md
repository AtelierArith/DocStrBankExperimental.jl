```
add_node_attribute!(datagraph, attribute, default_weight = 0.0)
add_node_attribute!(datadigraph, attribute, default_weight = 0.0)
```

Add a column filled with `default_weight` to the `node_data` matrix with the name `attribute`. If `attribute` already exists in the node data, an error is thrown.
