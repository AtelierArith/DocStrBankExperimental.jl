```
bymap(f, args...)
```

Uncertainty propagation using the `map` function.

Call `f` with particles or vectors of particles by using `map`. This can be utilized if registering `f` using [`register_primitive`](@ref) fails. See also [`Workspace`](@ref) if `bymap` fails.
