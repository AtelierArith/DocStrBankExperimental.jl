```
get_edge_data(g::BipartiteFactorGraph{TVar,TFac,E}, v1::Int, v2::Int) where {TVar,TFac,E}
```

Get data associated with edge between nodes `v1` and `v2`. Since the graph is undirected, the order of `v1` and `v2` doesn't matter.
