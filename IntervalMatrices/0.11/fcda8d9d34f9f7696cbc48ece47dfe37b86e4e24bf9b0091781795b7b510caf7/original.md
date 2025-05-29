```
scale(A::IntervalMatrix{T}, α::T) where {T}
```

Return a new interval matrix whose entries are scaled by the given factor.

### Input

  * `A` – interval matrix
  * `α` – scaling factor

### Output

A new matrix `B` of the same shape as `A` such that `B[i, j] = α*A[i, j]` for each `i` and `j`.

### Notes

See `scale!` for the in-place version of this function.
