```
low_connectivity([rng], [T], dims...;
                 return_sparse = false, connected=false,
                 in_degree = 1, radius = 1.0, cut_cycle = false)
```

Construct an internal reservoir connectivity matrix with low connectivity.

This function creates a square reservoir matrix with the specified in-degree for each node [^griffith2019]. When `in_degree` is 1, the function can enforce a fully connected cycle if `connected` is `true`; otherwise, it generates a random connectivity pattern.

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the reservoir matrix.

# Keyword Arguments

  * `return_sparse`: If `true`, the function returns the reservoir matrix as a sparse matrix. Default is `false`.
  * `connected`: For `in_degree == 1`, if `true` a connected cycle is enforced. Default is `false`.
  * `in_degree`: The number of incoming connections per node. Must not exceed the number of nodes. Default is 1.
  * `radius`: The desired spectral radius of the reservoir. Defaults to 1.0.
  * `cut_cycle`: If `true`, removes one edge from the cycle to cut it. Default is `false`.

[^griffith2019]: Griffith, Aaron, Andrew Pomerance, and Daniel J. Gauthier. "Forecasting chaotic systems with very low connectivity reservoir computers." Chaos: An Interdisciplinary Journal of Nonlinear Science 29.12 (2019).
