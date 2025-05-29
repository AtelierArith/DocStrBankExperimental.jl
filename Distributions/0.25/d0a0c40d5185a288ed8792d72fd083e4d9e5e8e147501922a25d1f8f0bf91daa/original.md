```
sqmahal(d, x)
```

Return the squared Mahalanobis distance from x to the center of d, w.r.t. the covariance. When x is a vector, it returns a scalar value. When x is a matrix, it returns a vector of length size(x,2).

`sqmahal!(r, d, x)` with write the results to a pre-allocated array `r`.
