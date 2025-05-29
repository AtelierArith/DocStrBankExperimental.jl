```
var_coordinates(data::DataMatrix)
```

Returns a matrix with coordinates for the variables. Only available for DataMatrices that have a dual representation (e.g. SVD/PCA).

In the case of `SVD` (PCA), `var_coordinates` returns the principal components as unit vectors.
