```
Ar = restrict(A[, dims])
```

Perform two-fold reduction in size along the dimensions listed in `dims`, or all coordinates if `dims` is omitted.  It anti-aliases A, so is more accurate than a naive summation over 2×2×... blocks. `restrict` is normalized so as to approximately preserve the mean value of `A`.

Thought of as an operator, `restrict` is equal to the transpose of `prolong`.
