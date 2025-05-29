```
kmeans!(X, centers; [kwargs...]) -> KmeansResult
```

Update the current cluster `centers` ($d×k$ matrix, where $d$ is the dimension and $k$ the number of centroids) using the $d×n$ data matrix `X` (each column of `X` is a $d$-dimensional data point).

See [`kmeans`](@ref) for the description of optional `kwargs`.
