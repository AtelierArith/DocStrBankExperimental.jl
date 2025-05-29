```
set_gradient!(agst::AbstractGradientSolverState, M, p, X)
```

set the (current) gradient stored within an [`AbstractGradientSolverState`](@ref) to `X`. The default function modifies `s.X`.
