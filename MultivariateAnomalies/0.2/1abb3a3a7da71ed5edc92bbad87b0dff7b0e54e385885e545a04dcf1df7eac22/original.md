```
init_knn_dists(T::Int, k::Int)
init_knn_dists(datacube::AbstractArray, k::Int)
```

initialize a preallocated `knn_dists_out` object. `k`is the number of nerarest neighbors, `T` the number of time steps (i.e. size of the first dimension) or a multidimensional `datacube`.
