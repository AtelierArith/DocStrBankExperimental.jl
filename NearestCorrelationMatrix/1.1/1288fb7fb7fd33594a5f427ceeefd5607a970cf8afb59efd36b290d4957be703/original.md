```
DirectProjection(; tau=eps())
```

Single step projection of the input matrix into the set of correlation matrices. Useful when a "close" correlation matrix is needed without concern for it being the most optimal.

# Parameters

  * `tau`: a tuning parameter controlling the smallest eigenvalue of the resulting matrix
