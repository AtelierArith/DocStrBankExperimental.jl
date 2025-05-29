```
cov(d::MatrixDistribution, flattened = Val(false))
```

Compute the 4-dimensional array whose `(i, j, k, l)` element is `cov(X[i,j], X[k, l])`.
