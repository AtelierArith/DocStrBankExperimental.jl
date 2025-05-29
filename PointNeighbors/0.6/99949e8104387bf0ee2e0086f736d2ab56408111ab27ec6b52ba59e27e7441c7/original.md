```
TrivialNeighborhoodSearch{NDIMS}(; search_radius = 0.0, eachpoint = 1:0,
                                 periodic_box = nothing)
```

Trivial neighborhood search that simply loops over all points.

# Arguments

  * `NDIMS`: Number of dimensions.

# Keywords

  * `search_radius = 0.0`:    The fixed search radius. The default of `0.0` is useful together                           with [`copy_neighborhood_search`](@ref).
  * `eachpoint = 1:0`:        Iterator for all point indices. Usually just `1:n_points`.                           The default of `1:0` is useful together with                           [`copy_neighborhood_search`](@ref).
  * `periodic_box = nothing`: In order to use a (rectangular) periodic domain, pass a                           [`PeriodicBox`](@ref).
