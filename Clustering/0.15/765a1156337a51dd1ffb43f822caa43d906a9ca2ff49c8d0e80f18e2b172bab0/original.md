```
kmeans(X, k, [...]) -> KmeansResult
```

K-means clustering of the $d×n$ data matrix `X` (each column of `X` is a $d$-dimensional data point) into `k` clusters.

# Arguments

  * `init` (defaults to `:kmpp`): how cluster seeds should be initialized, could be one of the following:

      * a `Symbol`, the name of a seeding algorithm (see [Seeding](@ref) for a list of supported methods);
      * an instance of [`SeedingAlgorithm`](@ref);
      * an integer vector of length $k$ that provides the indices of points to use as initial seeds.
  * `weights`: $n$-element vector of point weights (the cluster centers are the weighted means of cluster members)
  * `maxiter`, `tol`, `display`: see [common options](@ref common_options)
