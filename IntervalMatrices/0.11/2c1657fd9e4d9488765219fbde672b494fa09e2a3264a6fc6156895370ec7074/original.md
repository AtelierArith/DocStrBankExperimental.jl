```
hull(A::IntervalMatrix, B::IntervalMatrix)
```

Finds the interval hull of two interval matrices. This is equivalent to [`∪`](@ref).

### Input

  * `A` – interval matrix
  * `B` – interval matrix (of the same shape as `A`)

### Output

A new matrix `C` of the same shape as `A` such that `C[i, j] = hull(A[i, j], B[i, j])` for each `i` and `j`.
