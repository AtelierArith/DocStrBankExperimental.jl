```
BipartiteIndexedGraph{T<:Integer} <: AbstractIndexedGraph{T}
```

A type representing a sparse, undirected bipartite graph.

### FIELDS

  * `A` – adjacency matrix filled with `NullNumber`s. Rows are vertices belonging to the left block, columns to the right block
  * `X` – square matrix for efficient access by row. `X[j,i]` points to the index of element `A[i,j]` in `A.nzval`.
