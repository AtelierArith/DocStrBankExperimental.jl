```
set_gradient!(s::AbstractManoptSolverState, M::AbstractManifold, p, X)
```

set the gradient within an (possibly decorated) [`AbstractManoptSolverState`](@ref) to some (start) value `X` in the tangent space at `p`.
