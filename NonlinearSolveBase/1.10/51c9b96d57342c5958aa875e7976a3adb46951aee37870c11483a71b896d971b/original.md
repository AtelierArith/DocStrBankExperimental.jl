```
NonlinearSolveBase.NormTerminationMode <: AbstractNonlinearTerminationMode
```

Terminates if $\| \Delta u \| \leq reltol \times \| \Delta u + u \|$ or $\| \Delta u \| \leq abstol$. .

$\Delta u$ denotes the increment computed by the inner nonlinear solver.

## Constructor

```
NonlinearSolveBase.NormTerminationMode(internalnorm = nothing)
```

where `internalnorm` is the norm to use for the termination condition. Special handling is done for `norm(_, 2)`, `norm`, `norm(_, Inf)`, and `maximum(abs, _)`..
