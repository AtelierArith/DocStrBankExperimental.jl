```
x = triu2vec(Q; rowwise = false, her = false)
```

Reshape the upper triangular part of the `nxn` array `Q` as a one-dimensional column vector `x` with `n(n+1)/2` elements. `Q` is assumed symmetric/hermitian if `her = true`. The elements of `x` correspond to stacking the elements of successive columns of the upper triangular part of `Q`, if `rowwise = false`, or stacking the elements of successive rows of the upper triangular part of `Q`, if `rowwise = true`.
