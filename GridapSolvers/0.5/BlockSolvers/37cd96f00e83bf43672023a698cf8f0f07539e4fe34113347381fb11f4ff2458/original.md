```
function BlockDiagonalSolver(
  solvers::AbstractVector{<:LinearSolver}; 
  is_nonlinear::Vector{Bool}=fill(false,length(solvers))
)
```

Create and instance of [`BlockDiagonalSolver`](@ref) where all blocks are extracted from  the linear system.
