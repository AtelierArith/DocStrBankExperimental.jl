```
decompress(
    spline_dimension::SplineDimension{Tv}; derivative_order::Integer = 0) where {Tv}
```

Transform `spline_dimension.eval` into a matrix of shape `(n_sample_points, n_points - degree - 1)` which explicitly gives the value for each basis function at each sample point.
