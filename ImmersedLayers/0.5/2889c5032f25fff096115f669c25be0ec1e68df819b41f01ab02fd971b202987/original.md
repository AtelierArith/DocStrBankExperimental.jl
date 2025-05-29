```
create_CL2invCT(cache::BasicILMCache[;scale=1.0])
```

Using the provided cache `cache`, construct the square matrix $-C_s L^{-2} C_s^T$, which maps data of the primary point data type of the cache to data of the same type. The operators `C_s` and `C_s^T` correspond to [`surface_curl!`](@ref) and `L` is the grid Laplacian. The optional keyword `scale` multiplies the matrix by the designated value.
