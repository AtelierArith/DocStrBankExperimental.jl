```
Graphs.inneighbors(g::SimpleWeightedDiGraph, v)
```

Return the vector of inneighbors of vertex `v`.

!!! tip "Performance"
    This function is less efficient than `inneighbors` for directed weighted graphs (it allocates a new vector).

