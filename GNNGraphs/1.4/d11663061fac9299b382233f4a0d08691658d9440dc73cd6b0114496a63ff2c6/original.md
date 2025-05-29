```
graph_indicator(g::GNNGraph; edges=false)
```

Return a vector containing the graph membership (an integer from `1` to `g.num_graphs`) of each node in the graph. If `edges=true`, return the graph membership of each edge instead.
