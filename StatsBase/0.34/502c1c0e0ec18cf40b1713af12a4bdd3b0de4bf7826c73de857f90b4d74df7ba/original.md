```
genvar(X)
```

Compute the generalized sample variance of `X`. If `X` is a vector, one-column matrix, or other iterable, this is equivalent to the sample variance. Otherwise if `X` is a matrix, this is equivalent to the determinant of the covariance matrix of `X`.

!!! note
    The generalized sample variance will be 0 if the columns of the matrix of deviations are linearly dependent.

