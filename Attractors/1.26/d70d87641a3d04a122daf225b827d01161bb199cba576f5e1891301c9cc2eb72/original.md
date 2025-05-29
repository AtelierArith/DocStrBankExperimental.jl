```
convergence_time(mapper::AttractorMapper) → t
```

Return the approximate time the `mapper` took to converge to an attractor. This function should be called just right after `mapper(u0)` was called with `u0` the initial condition of interest. Hence it is only valid with `AttractorMapper` subtypes that support this syntax.

Obtaining the convergence time is computationally free, so that [`convergence_and_basins_fractions`](@ref) can always be used instead of [`basins_fractions`](@ref).
