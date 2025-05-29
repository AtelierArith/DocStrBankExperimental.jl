```
plausible_ic_sampler(ds::DynamicalSystem [, seed])
```

Return a `sampler` that can be called as a 0-argument function `sampler()`, which yields random initial conditions within the hyperrectangle defined by the [`plausible_limits`](@ref) of `ds`. The `sampler` is useful to give to e.g., `DynamicalSystems.basins_fractions`.
