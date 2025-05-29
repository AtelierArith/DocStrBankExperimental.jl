```
create_RTLinvR(cache::BasicILMCache[;scale=1.0])
```

Using the provided cache `cache`, construct the square matrix $-R^T L^{-1}R$, which maps data of type `ScalarData` to data of the same type. The operators `R^T` and `R` correspond to [`interpolate!`](@ref) and [`regularize!`](@ref) and `L^{-1}` is the inverse of the grid Laplacian. The optional keyword `scale` multiplies the matrix by the designated value.
