```
bdplot_boundarymap(bmap, intervals; figkwargs = NamedTuple(), kwargs...)
```

Plot the output of [`DynamicalBilliards.boundarymap`](@ref) into an axis that correctly displays information about obstacle arclengths. Return `figure, axis`.

Also works for the parallelized version of boundary map.

## Keyword Arguments

  * `figkwargs = NamedTuple()` keywords propagated to `Figure`.
  * `color` : The color to use for the plotted points. Can be either a single color or a vector of colors of length `length(bmap)`, in order to give each initial condition a different color (for parallelized version).
  * All other keywords propagated to `scatter!`.
