```
filter_nodes(datadigraph, filter_value, attribute = dg.node_data.attributes[1]; fn = isless)
```

Removes the nodes of the graph whose data on `attribute` is does not meet the criteria of `fn` with respect to `filter_value`. If `attribute` is not specified, this defaults to the first attribute within the DataDiGraph's `NodeData`.

`fn` is a function that takes an input of a node's data on attribute and the `filter_value` and returns a true or false
