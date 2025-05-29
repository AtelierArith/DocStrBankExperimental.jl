```
function BlockDiagonalSolver(
  funcs   :: AbstractArray{<:Function},
  trials  :: AbstractArray{<:FESpace},
  tests   :: AbstractArray{<:FESpace},
  solvers :: AbstractArray{<:LinearSolver};
  is_nonlinear::Vector{Bool}=fill(false,length(solvers))
)
```

Create and instance of [`BlockDiagonalSolver`](@ref) where all blocks are given by  integral forms.
