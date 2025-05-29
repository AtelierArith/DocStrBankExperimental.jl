```
set_iterate!(agst::AbstractGradientSolverState, M, p)
```

set the (current) iterate stored within an [`AbstractGradientSolverState`](@ref) to `p`. The default function modifies `s.p`.
