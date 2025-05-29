```
Solver(path_tracker; seed = nothing)
```

A struct containing multiple copies of `path_tracker`. This contains all pre-allocated data structures to call [`solve`]. The most convenient way to construct a `Solver` is via [`solver_startsolutions`](@ref).
