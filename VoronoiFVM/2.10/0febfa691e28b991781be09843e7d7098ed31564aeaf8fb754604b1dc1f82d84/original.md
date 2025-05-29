```julia
calc_divergences(sys, evelo, bfvelo)

```

Calculate for each Voronoi cell associated with a node of sys.grid the divergence of the velocity field used to obtain `evelo` and `bfvelo` via  [`edgevelocities`](@ref) and [`bfacevelocities`](@ref) by means of summing all `evelos` and `bfvelos` per Voronoi cell.
