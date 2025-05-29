```
MetaGraph(
    graph,
    label_type,
    vertex_data_type=Nothing,
    edge_data_type=Nothing,
    graph_data=nothing,
    weight_function=edge_data -> 1.0,
    default_weight=1.0
)
```

Construct an empty `MetaGraph` based on an empty `graph`, initializing storage with metadata types *given as positional arguments*.
