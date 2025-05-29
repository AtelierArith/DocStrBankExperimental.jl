```
matrix2graph(sparse_matrix, [partition_by_rows::Bool=true])
```

A utility function to generate a graph from input sparse matrix, columns are represented with vertices and 2 vertices are connected with an edge only if the two columns are mutually orthogonal.

Note that the sparsity pattern is defined by structural nonzeroes, ie includes explicitly stored zeros.
