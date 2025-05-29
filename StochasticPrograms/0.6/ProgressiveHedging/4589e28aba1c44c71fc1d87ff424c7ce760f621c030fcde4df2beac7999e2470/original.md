```
ProgressiveHedgingAlgorithm
```

Functor object for the progressive-hedging algorithm. Create using the `ProgressiveHedgingSolver` factory function and then pass to a `StochasticPrograms.jl` model.

...

# Parameters

  * `τ::AbstractFloat = 1e-6`: Relative tolerance for convergence checks.
  * `log::Bool = true`: Specifices if progressive-hedging procedure should be logged on standard output or not.

...
