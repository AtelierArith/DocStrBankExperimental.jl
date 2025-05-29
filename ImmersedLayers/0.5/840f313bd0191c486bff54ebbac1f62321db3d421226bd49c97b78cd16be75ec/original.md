```
create_GLinvD(cache::BasicILMCache[;scale=1.0])
```

Using the provided cache `cache`, construct the square matrix $-G_s L^{-1}D_s$, which maps data of type `ScalarData` to data of the same type. The operators `G_s` and `D_s` correspond to [`surface_grad!`](@ref) and [`surface_divergence!`](@ref), and `L` is the grid Laplacian. The optional keyword `scale` multiplies the matrix by the designated value.
