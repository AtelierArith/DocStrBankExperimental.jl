```
function BlockDiagonalSolver(
  blocks  :: AbstractVector{<:SolverBlock},
  solvers :: AbstractVector{<:LinearSolver}
)
```

Create and instance of [`BlockDiagonalSolver`](@ref) from its underlying properties.
