```
q_space_path(cryst::Crystal, qs, n; labels=nothing)
```

Returns a 1D path consisting of `n` wavevectors sampled piecewise-linearly between the points in `qs`. Although the `qs` are provided in reciprocal lattice units (RLU), consecutive samples are spaced uniformly in the global (inverse-length) Cartesian coordinate system. Optional `labels` can be associated with each special q-point, and will be used in plotting functions.

See also [`q_space_grid`](@ref).
