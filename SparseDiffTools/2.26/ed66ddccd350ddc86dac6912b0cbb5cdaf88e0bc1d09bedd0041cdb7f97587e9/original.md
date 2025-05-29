```
matrix_colors(A, alg::ColoringAlgorithm = GreedyD1Color();
    partition_by_rows::Bool = false)
```

Return the colorvec vector for the matrix A using the chosen coloring algorithm. If a known analytical solution exists, that is used instead. The coloring defaults to a greedy distance-1 coloring.

Note that if A isa SparseMatrixCSC, the sparsity pattern is defined by structural nonzeroes, ie includes explicitly stored zeros.

If `ArrayInterface.fast_matrix_colors(A)` is true, then uses `ArrayInterface.matrix_colors(A)` to compute the matrix colors.
