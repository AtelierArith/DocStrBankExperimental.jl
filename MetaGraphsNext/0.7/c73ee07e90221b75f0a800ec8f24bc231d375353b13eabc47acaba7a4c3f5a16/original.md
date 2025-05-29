```
add_edge!(meta_graph, label_1, label_2, data)
```

Add an edge `(label_1, label_2)` to MetaGraph `meta_graph` with metadata `data`. If the `EdgeData` type of `meta_graph` is `Nothing`, `data` can be omitted.

Return `true` if the edge has been added, `false` otherwise. If one of the labels does not exist, nothing happens and `false` is returned (the label is not inserted). If `(label_1, label_2)` already exists, its data is updated to `data` and `false` is returned nonetheless.
