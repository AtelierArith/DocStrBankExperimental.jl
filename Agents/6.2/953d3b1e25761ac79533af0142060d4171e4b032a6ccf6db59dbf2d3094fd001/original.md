```
ensemblerun!(generator, n; kwargs...)
```

Generate many `ABM`s and propagate them into `ensemblerun!(models, ...)` using the provided `generator` which is a one-argument function whose input is a seed.

This method has additional keywords `ensemble = 5, seeds = rand(UInt32, ensemble)`.
