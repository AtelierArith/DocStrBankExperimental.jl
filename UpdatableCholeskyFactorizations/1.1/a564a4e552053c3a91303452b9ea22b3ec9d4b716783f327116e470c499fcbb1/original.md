```
remove_column!(C::UpdatableCholesky, i::Int)
```

updating `UpdatableCholesky` factorization `C` corresponding to removal of the `i`th row and column of the original matrix. Complexity is `O(n²)`.
