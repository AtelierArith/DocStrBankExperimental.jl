```
BROptions
```

Struct to contain options for `best_response`.

# Fields

  * `tol::Real=1e-8` : Tolerance level.
  * `tie_breaking::Symbol=:smallest` : `:smallest` or `:random`.
  * `rng::AbstractRNG=GLOBAL_RNG` : Random number generator.
