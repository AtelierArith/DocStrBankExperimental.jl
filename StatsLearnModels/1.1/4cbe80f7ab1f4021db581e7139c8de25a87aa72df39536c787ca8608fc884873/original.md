```
KNNRegressor(k, metric=Euclidean(); leafsize=10, reorder=true)
```

K-nearest neighbor regression model with `k` neighbors and `metric` from Distances.jl. Optionally, specify the `leafsize` and `reorder` options for the underlying trees in [NearestNeighbors.jl](https://github.com/KristofferC/NearestNeighbors.jl).

See also [`KNNClassifier`](@ref).
