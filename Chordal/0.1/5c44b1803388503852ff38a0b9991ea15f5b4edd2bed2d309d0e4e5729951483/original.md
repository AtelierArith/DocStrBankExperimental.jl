```
get_selectors(input_mat::SparseMatrixCSC; verbose=true, ret_cliques=true)
```

Returns the (merged) cliques of the graph corresponding to the sparsity pattern of `input_mat` (after a permutation to reduce fill-in) and optionally the cliques. Also returns the fill-reducing permutation and and inverse permutation used.
