```
edges(g::BipartiteFactorGraph)
```

Get all edges in the graph. 

!!! note
    This function behaves differently from `variables` and `factors` in that it calls `Graphs.edges`.  The closest equivalent for nodes is the `neighbors` function.

