```
convergence_and_basins_of_attraction(mapper::AttractorMapper, grid)
```

An extension of [`basins_of_attraction`](@ref). Return `basins, attractors, convergence`, with `basins, attractors` as in `basins_of_attraction`, and `convergence` being an array with same shape as `basins`. It contains the time each initial condition took to converge to its attractor. It is useful to give to [`shaded_basins_heatmap`](@ref).

See also [`convergence_time`](@ref).

# Keyword arguments

  * `show_progress = true`: show progress bar.
