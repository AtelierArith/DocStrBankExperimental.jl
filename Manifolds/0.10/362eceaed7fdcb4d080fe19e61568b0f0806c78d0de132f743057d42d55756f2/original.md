```
manifold_dimension(M::KendallsShapeSpace)
```

Return the dimension of the [`KendallsShapeSpace`](@ref) manifold `M`. The dimension is given by $n(k - 1) - 1 - n(n - 1)/2$ in the typical case where $k \geq n+1$, and $(k + 1)(k - 2) / 2$ otherwise, unless $k$ is equal to 1, in which case the dimension is 0. See [Kendall:1984](@cite) for a discussion of the over-dimensioned case.
