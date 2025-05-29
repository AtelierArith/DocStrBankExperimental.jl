```
edge_indices(graph) -> CartesianIndices
```

各ノード `v` のKNNのインデックスをタプル (v, i) として返します。`node_edge(graph, v, i)` と一緒に使用します。
