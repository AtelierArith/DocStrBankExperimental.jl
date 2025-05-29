```
PrecomputedNeighborhoodSearch{NDIMS}(; search_radius = 0.0, n_points = 0,
                                     periodic_box = nothing, update_strategy = nothing)
```

Neighborhood search with precomputed neighbor lists. A list of all neighbors is computed for each point during initialization and update. This neighborhood search maximizes the performance of neighbor loops at the cost of a much slower [`update!`](@ref).

A [`GridNeighborhoodSearch`](@ref) is used internally to compute the neighbor lists during initialization and update.

# Arguments

  * `NDIMS`: Number of dimensions.

# Keywords

  * `search_radius = 0.0`:    The fixed search radius. The default of `0.0` is useful together                           with [`copy_neighborhood_search`](@ref).
  * `n_points = 0`:           Total number of points. The default of `0` is useful together                           with [`copy_neighborhood_search`](@ref).
  * `periodic_box = nothing`: In order to use a (rectangular) periodic domain, pass a                           [`PeriodicBox`](@ref).
  * `update_strategy`:        Strategy to parallelize `update!` of the internally used                           `GridNeighborhoodSearch`. See [`GridNeighborhoodSearch`](@ref)                           for available options.
