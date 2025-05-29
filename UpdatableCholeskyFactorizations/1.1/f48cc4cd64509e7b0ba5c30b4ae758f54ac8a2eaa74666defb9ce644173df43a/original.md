```
add_column!(C::UpdatableCholesky, A::AbstractMatrix)
```

appending columns in A - and their corresponding rows A' - to `UpdatableCholesky`  factorization `C`. Complexity is `O(m³ + n²m)` where `n = size(C, 1)` and `m = size(A, 2)`.
