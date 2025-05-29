```
init_residual(cf::T; t=NaN, recalc=false)
```

Calculates the residual |du| for the given component model for the values provided via `default` and `init` [Metadata](@ref).

If recalc=false just return the residual determined in the actual initialization process.

See also [`initialize_component!`](@ref).
