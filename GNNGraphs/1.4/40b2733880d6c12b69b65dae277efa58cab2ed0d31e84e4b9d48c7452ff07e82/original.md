```
adjacency_matrix(g::GNNGraph, T=eltype(g); dir=:out, weighted=true)
```

Return the adjacency matrix `A` for the graph `g`. 

If `dir=:out`, `A[i,j] > 0` denotes the presence of an edge from node `i` to node `j`. If `dir=:in` instead, `A[i,j] > 0` denotes the presence of an edge from node `j` to node `i`.

User may specify the eltype `T` of the returned matrix. 

If `weighted=true`, the `A` will contain the edge weights if any, otherwise the elements of `A` will be either 0 or 1.
