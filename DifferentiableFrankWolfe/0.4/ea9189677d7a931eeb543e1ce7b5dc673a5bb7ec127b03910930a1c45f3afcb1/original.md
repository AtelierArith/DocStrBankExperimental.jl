```
(dfw::DiffFW)(θ::AbstractArray, frank_wolfe_kwargs::NamedTuple)
```

Apply the Frank-Wolfe algorithm to `θ` with settings defined by the named tuple `frank_wolfe_kwargs` (given as a positional argument).

Return a couple (x, stats) where `x` is the solution and `stats` is a named tuple containing additional information (its contents are not covered by public API, and mostly useful for debugging).
