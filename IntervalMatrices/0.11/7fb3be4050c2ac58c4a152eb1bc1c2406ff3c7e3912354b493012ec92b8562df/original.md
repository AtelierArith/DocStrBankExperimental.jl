```
scale!(A::IntervalMatrix{T}, α::T) where {T}
```

Modifies the given interval matrix, scaling its entries by the given factor.

### Input

  * `A` – interval matrix
  * `α` – scaling factor

### Output

The matrix `A` such that for each `i` and `j`, the new value of `A[i, j]` is `α*A[i, j]`.

### Notes

This is the in-place version of `scale`.
