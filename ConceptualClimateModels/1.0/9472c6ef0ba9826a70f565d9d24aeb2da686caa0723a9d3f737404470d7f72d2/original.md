```
plausible_grid(ds::DynamicalSystem, n = 101)
```

Return a `grid` that is a tuple of `range` objects that each spans the [`plausible_limits`](@ref)(`ds`). `n` can be an integer or a vector of integers (for each dimension). The resulting `grid` is useful to give to `DynamicalSystems.AttractorsViaRecurrences`.
