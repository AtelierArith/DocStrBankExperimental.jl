```
function BlockDiagonalSolver(
  solvers::AbstractVector{<:LinearSolver}; 
  is_nonlinear::Vector{Bool}=fill(false,length(solvers))
)
```

線形系からすべてのブロックが抽出された[`BlockDiagonalSolver`](@ref)のインスタンスを作成します。
