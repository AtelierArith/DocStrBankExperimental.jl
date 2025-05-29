```
create_GLinvD_cross(cache::BasicILMCache[;scale=1.0])
```

Using the provided cache `cache`, construct the square matrix $-\hat{G}_s L^{-1}\hat{D}_s$, which maps data of type `ScalarData` to data of the same type. The operators `G_s` and `D_s` correspond to [`surface_grad_cross!`](@ref) and [`surface_divergence_cross!`](@ref), and `L` is the grid Laplacian. The optional keyword `scale` multiplies the matrix by the designated value.
