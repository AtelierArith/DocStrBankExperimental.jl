```
init_sparsity_pattern(dh::DofHandler; nnz_per_row::Int)
```

Initialize an empty [`SparsityPattern`](@ref) with `ndofs(dh)` rows and `ndofs(dh)` columns.

# Keyword arguments

  * `nnz_per_row`: memory optimization hint for the number of non-zero entries per row that will be added to the pattern.
