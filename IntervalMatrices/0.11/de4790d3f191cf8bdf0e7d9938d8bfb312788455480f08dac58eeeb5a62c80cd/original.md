```
diam(A::IntervalMatrix{T}) where {T}
```

Return a matrix whose entries describe the diameters of the intervals.

### Input

  * `A` – interval matrix

### Output

A matrix `B` of the same shape as `A` such that `B[i, j] == diam(A[i, j])` for each `i` and `j`.
