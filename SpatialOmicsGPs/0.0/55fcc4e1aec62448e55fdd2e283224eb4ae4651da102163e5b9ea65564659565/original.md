```
lengthscales(X, n=10)
```

For a vector-of-vectors `X`, return a grid of length scales with `n` grid points, logarithmically spaced.  The boundaries of the grid are by default set as the shortest observed distance between pairs of vectors in `X` divided by 2, and the longest observed distance`between pairs of vectors in`X` multiplied by 2.

The input `X` should be of type `RowVecs` or `ColVecs` from the `KernelFunctions` package.
