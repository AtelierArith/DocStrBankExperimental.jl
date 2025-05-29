```
MetaGraph(
    graph,
    vertices_description,
    edges_description,
    graph_data=nothing,
    weight_function=edge_data -> 1.0,
    default_weight=1.0,
)
```

Construct a non-empty `MetaGraph` based on a non-empty `graph` with specified vertex and edge data, *given as positional arguments*.

The data must be given as follows:

  * `vertices_description` is a vector of pairs `label => data` (the code of a vertex will correspond to its rank in the list)
  * `edges_description` is a vector of pairs `(label1, label2) => data`

Furthermore, these arguments must be coherent with the `graph` argument, i.e. describe the same set of vertices and edges.
