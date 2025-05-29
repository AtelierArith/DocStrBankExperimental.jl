```
is_alternating(M::MatrixElem)
```

Return whether the form corresponding to the matrix `M` is alternating, i.e. `M = -transpose(M)` and `M` has zeros on the diagonal. Return `false` if `M` is not a square matrix.
