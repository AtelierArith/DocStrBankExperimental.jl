```
function BlockDiagonalSolver(
  mats::AbstractVector{<:AbstractMatrix},
  solvers::AbstractVector{<:LinearSolver}
)
```

Create and instance of [`BlockDiagonalSolver`](@ref) where all blocks are given by  external matrices.
