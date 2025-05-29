```
shaded_basins_heatmap(grid, basins, attractors, iterations; kwargs...)
```

Plot a heatmap of found (2-dimensional) `basins` of attraction and corresponding `attractors`. A matrix `iterations` with the same size of `basins` must be provided to shade the color according to the value of this matrix. A small value corresponds to a light color and a large value to a darker tone. This is useful to represent the number of iterations taken for each initial condition to converge. See also [`convergence_time`](@ref) to store this iteration number.

## Keyword arguments

  * `show_attractors = true`: shows the attractor on plot
  * `maxit = maximum(iterations)`: clip the values of `iterations` to

the value `maxit`. Useful when there are some very long iterations and keep the range constrained to a given interval.

  * All the [common plotting keywords](@ref common_plot_kwargs).
