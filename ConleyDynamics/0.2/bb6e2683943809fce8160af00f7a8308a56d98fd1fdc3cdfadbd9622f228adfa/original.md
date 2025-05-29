```
sparse_permute(sm::SparseMatrix, pr::Vector{Int}, pc::Vector{Int})
```

Create sparse matrix by permuting the row and column indices.

The vector `pr` describes the row permutation, and `pc` the column permutation.
