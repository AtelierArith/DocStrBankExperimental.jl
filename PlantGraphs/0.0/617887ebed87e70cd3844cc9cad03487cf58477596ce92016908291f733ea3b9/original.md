```
node_label(n::Node, id)
```

Function to construct a label for a node to be used by `draw()` when visualizing. The user can specialize this method for user-defined data types to customize the labels. By default, the type of data stored in the node and the unique ID of the node are used as labels.
