```
NonlinearSolveBase.RelNormSafeTerminationMode <: NonlinearSolveBase.AbstractSafeNonlinearTerminationMode
```

Essentially [`RelNormTerminationMode`](@ref) + terminate if there has been no improvement for the last `patience_steps` + terminate if the solution blows up (diverges).

## Constructor

```
NonlinearSolveBase.RelNormSafeTerminationMode(
    internalnorm; protective_threshold = nothing,
    patience_steps = 100, patience_objective_multiplier = 3,
    min_max_factor = 1.3, max_stalled_steps = nothing
)
```

where `internalnorm` is the norm to use for the termination condition. Special handling is done for `norm(_, 2)`, `norm`, `norm(_, Inf)`, and `maximum(abs, _)`..
