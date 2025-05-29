```
function BlockDiagonalSolver(
  funcs   :: AbstractArray{<:Function},
  trials  :: AbstractArray{<:FESpace},
  tests   :: AbstractArray{<:FESpace},
  solvers :: AbstractArray{<:LinearSolver};
  is_nonlinear::Vector{Bool}=fill(false,length(solvers))
)
```

[`BlockDiagonalSolver`](@ref) のインスタンスを作成します。すべてのブロックは積分形式によって与えられます。
