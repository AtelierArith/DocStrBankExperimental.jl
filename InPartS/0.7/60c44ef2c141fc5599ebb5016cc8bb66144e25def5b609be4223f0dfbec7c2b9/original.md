```
autogrid!(sim, lsize, params, spacing = 1.0, rng = sim.rng, kwargs...)
```

Add particles arranged on an `N`-dimensional Cartesian lattice to `sim`.

This essentially calls addgrid!, but chooses `distance` as the maximum `minimumgridconstant` for any of the specified parameters (multiplied by `spacing`) and initializes particles with the model-defined `defaultgridinitialization` function.

`rng` is used as the `_jitter_rng` for `addgrid!` and passed to `defaultgridinitialization`.
