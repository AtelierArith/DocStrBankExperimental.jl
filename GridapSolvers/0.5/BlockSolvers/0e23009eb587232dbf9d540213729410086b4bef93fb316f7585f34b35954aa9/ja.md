```
function BlockDiagonalSolver(
  mats::AbstractVector{<:AbstractMatrix},
  solvers::AbstractVector{<:LinearSolver}
)
```

外部行列によって与えられたすべてのブロックを持つ[`BlockDiagonalSolver`](@ref)のインスタンスを作成します。
