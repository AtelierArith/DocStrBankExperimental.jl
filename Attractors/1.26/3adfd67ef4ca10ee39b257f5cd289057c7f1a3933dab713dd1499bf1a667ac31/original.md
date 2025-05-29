```
subdivision_based_grid(ds::DynamicalSystem, grid; maxlevel = 4, q = 0.99)
```

Construct a grid structure [`SubdivisionBasedGrid`](@ref) that can be directly passed as a grid to [`AttractorsViaRecurrences`](@ref). The input `grid` is an originally coarse grid (a tuple of `AbstractRange`s). The state space speed is evaluate in all cells of the `grid`. Cells with small speed (when compared to the "max" speed) resultin in this cell being subdivided more. To avoid problems with spikes in the speed, the `q`-th quantile of the velocities is used as the "max" speed (use `q = 1` for true maximum). The subdivisions in the resulting grid are clamped to at most value `maxlevel`.

This approach is designed for *continuous time* systems in which different areas of the state space flow may have significantly different velocity. In case of originally coarse grids, this may lead [`AttractorsViaRecurrences`](@ref) being stuck in some state space regions with a small motion speed and false identification of attractors.
