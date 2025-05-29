```
convergence_and_basins_fractions(mapper::AttractorMapper, ics)
```

An extension of [`basins_fractions`](@ref). Return `fs, labels, convergence`. The first two are as in `basins_fractions`, and `convergence` is a vector containing the time each initial condition took to converge to its attractor. Only usable with mappers that support `id = mapper(u0)`.

See also [`convergence_time`](@ref).

# Keyword arguments

  * `show_progress = true`: show progress bar.
