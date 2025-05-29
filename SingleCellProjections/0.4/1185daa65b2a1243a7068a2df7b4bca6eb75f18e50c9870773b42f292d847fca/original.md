```
obs_coordinates(data::DataMatrix)
```

Returns a matrix with coordinates for the observations. Not available for all types of DataMatrices. Mostly useful for data matrices after dimension reduction such as `svd` or `force_layout` has been applied.

In the case of `SVD` (PCA), `obs_coordinates` returns the principal components, scaled by the singular values. This is a a good starting point for downstream analysis, since it is the optimal linear approximation of the original data for the given number of dimensions.
