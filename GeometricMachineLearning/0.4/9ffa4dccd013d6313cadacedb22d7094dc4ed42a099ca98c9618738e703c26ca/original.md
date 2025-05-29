```
StiefelProjection(backend, T, N, n)
```

Make a matrix of the form $\begin{bmatrix} \mathbb{I} & \mathbb{O} \end{bmatrix}^T$ for a specific backend and data type.

An array that essentially does `vcat(I(n), zeros(N-n, n))` with GPU support. 

# Extended help

An instance of `StiefelProjection` should technically also belong to [`StiefelManifold`](@ref). 
