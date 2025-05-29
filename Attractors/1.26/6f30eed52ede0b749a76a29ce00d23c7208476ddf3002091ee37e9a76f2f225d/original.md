```
basins_of_attraction(mapper::AttractorMapper, grid::Tuple) → basins, attractors
```

Compute the full basins of attraction as identified by the given `mapper`, which includes a reference to a [`DynamicalSystem`](@ref) and return them along with (perhaps approximated) found attractors.

`grid` is a tuple of ranges defining the grid of initial conditions that partition the state space into boxes with size the step size of each range. For example, `grid = (xg, yg)` where `xg = yg = range(-5, 5; length = 100)`. The grid has to be the same dimensionality as the state space expected by the integrator/system used in `mapper`. E.g., a [`ProjectedDynamicalSystem`](@ref) could be used for lower dimensional projections, etc. A special case here is a [`PoincareMap`](@ref) with `plane` being `Tuple{Int, <: Real}`. In this special scenario the grid can be one dimension smaller than the state space, in which case the partitioning happens directly on the hyperplane the Poincaré map operates on.

`basins_of_attraction` function is a convenience 5-lines-of-code wrapper which uses the `labels` returned by [`basins_fractions`](@ref) and simply assigns them to a full array corresponding to the state space partitioning indicated by `grid`.

See also [`convergence_and_basins_of_attraction`](@ref).
