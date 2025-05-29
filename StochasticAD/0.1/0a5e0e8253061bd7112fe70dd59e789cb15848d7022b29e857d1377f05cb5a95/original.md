```
dual_number(X, p; backend=PrunedFIsBackend(), direction=nothing)
dual_number(p; backend=PrunedFIsBackend(), direction=nothing)
```

A lightweight wrapper around [`stochastic_triple`](#StochasticAD.stochastic_triple) that entirely ignores the derivative contribution of all discrete random components, so that it behaves like a regular dual number. Mostly for fun – this, of course, leads to a useless derivative estimate for discrete random functions!
