```
clique_projection(graph::OptiGraph)
```

Retrieve a standard graph representation of `graph`. The projection contains a standard `Graphs.Graph` and a mapping between its elements and the given optigraph. This projection works by creating an edge for each pair of nodes in each hyperedge.
