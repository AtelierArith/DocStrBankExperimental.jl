```
adjacency_matrix(g::BipartiteIndexedGraph, T::DataType=Int)
```

Return the symmetric adjacency matrix of size `nv(g) = nv_left(g) + nv_right(g)`  where no distinction is made between left and right nodes.
