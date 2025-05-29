```
Graphs.outneighbors(g::SimpleWeightedDiGraph, v)
```

Return the vector of outneighbors of vertex `v`.

!!! tip "Performance"
    This function is more efficient than `inneighbors` for directed weighted graphs.

