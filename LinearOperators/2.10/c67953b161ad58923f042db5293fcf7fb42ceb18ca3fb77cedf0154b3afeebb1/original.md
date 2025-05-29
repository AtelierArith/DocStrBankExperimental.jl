```
opInverse(M; symm=false, herm=false)
```

Inverse of a matrix as a linear operator using `\`. Useful for triangular matrices. Note that each application of this operator applies `\`. This Operator is not in-place when using `mul!`.
