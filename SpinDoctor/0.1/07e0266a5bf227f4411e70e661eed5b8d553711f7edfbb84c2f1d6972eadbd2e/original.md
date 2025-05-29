```
IntervalConstantSolver(; θ = 0.5, timestep)
```

BTPDE solver specialized on intervalwise constant `ScalarGradient`s, e.g [`PGSE`](@ref), [`DoublePGSE`](@ref). Raises an error for other gradients.
