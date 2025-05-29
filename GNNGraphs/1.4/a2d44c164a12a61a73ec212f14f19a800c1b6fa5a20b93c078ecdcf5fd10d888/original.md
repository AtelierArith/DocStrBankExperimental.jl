```
khop_adj(g::GNNGraph,k::Int,T::DataType=eltype(g); dir=:out, weighted=true)
```

Return $A^k$ where $A$ is the adjacency matrix of the graph 'g'.
