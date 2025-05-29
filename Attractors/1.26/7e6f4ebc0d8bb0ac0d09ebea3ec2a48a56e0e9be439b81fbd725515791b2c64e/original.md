```
plot_attractors(attractors::Dict{Int, StateSpaceSet}; kwargs...)
```

Plot the attractors as a scatter plot.

## Keyword arguments

  * All the [common plotting keywords](@ref common_plot_kwargs). Particularly important is the `access` keyword.
  * `sckwargs = (strokewidth = 0.5, strokecolor = :black,)`: additional keywords propagated to the `Makie.scatter` function that plots the attractors.
