```
IndexedGraph{T<:Integer} <: AbstractIndexedGraph{T}
```

A type representing a sparse undirected graph.

### FIELDS

  * `A` – square adjacency matrix. `A[i,j] == A[j,i]` contains the unique index associated to unidrected edge `(i,j)`
