```
tensor_to_graph(tensor, attribute)
```

Constructs a graph from a 3-D array (a tensor). Each entry of the tensor is represented by a node, and each node is connected to the adjacent nodes in each dimension. This function creates the graph structure and saves the values of the tensor to their corresponding nodes as weight values under the name `attribute`.
