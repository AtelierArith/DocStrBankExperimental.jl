```
kmedoids(dist::AbstractMatrix, k::Integer; ...) -> KmedoidsResult
```

Perform K-medoids clustering of $n$ points into `k` clusters, given the `dist` matrix ($n×n$, `dist[i, j]` is the distance between the `j`-th and `i`-th points).

# Arguments

  * `init` (defaults to `:kmpp`): how medoids should be initialized, could be one of the following:

      * a `Symbol` indicating the name of a seeding algorithm (see [Seeding](@ref Seeding) for a list of supported methods).
      * an integer vector of length `k` that provides the indices of points to use as initial medoids.
  * `maxiter`, `tol`, `display`: see [common options](@ref common_options)

# Note

The function implements a *K-means style* algorithm instead of *PAM* (Partitioning Around Medoids). K-means style algorithm converges in fewer iterations, but was shown to produce worse (10-20% higher total costs) results (see e.g. [Schubert & Rousseeuw (2019)](@ref kmedoid_refs)).
