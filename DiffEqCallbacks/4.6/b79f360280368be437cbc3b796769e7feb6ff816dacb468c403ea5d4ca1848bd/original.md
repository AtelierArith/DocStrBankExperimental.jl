```julia
AutoAbstol(save = true; init_curmax = 1e-6)
```

Provides a way to automatically adapt the absolute tolerance to the problem. This helps the solvers automatically “learn” what appropriate limits are. This callback set starts the absolute tolerance at `init_curmax` (default `1e-6`), and at each iteration it is set to the maximum value that the state has thus far reached times the relative tolerance.

## Keyword Arguments

  * `save` determines whether this callback has saving enabled
  * `init_curmax` is the initial `abstol`.

If this callback is used in isolation, `save=true` is required for normal saving behavior. Otherwise, `save=false` should be set to ensure extra saves do not occur.
