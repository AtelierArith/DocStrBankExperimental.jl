```
Q = vec2triu(x; rowwise = false, her = false)
```

Build from a one-dimensional column vector `x` with `n(n+1)/2` elements an `nxn` upper triangular matrix `Q` if `her = false` or an `nxn` symmetric/hermitian array `Q` if `her = true`. The elements of `x` correspond to stacking the elements of successive columns of the upper triangular part of `Q`, if `rowwise = false`, or stacking the elements of successive rows of the upper triangular part of `Q`, if `rowwise = true`.
