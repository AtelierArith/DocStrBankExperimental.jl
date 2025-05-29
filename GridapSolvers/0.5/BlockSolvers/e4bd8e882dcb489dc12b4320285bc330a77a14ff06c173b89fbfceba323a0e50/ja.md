```
function BlockDiagonalSolver(
  blocks  :: AbstractVector{<:SolverBlock},
  solvers :: AbstractVector{<:LinearSolver}
)
```

[`BlockDiagonalSolver`](@ref)の基になるプロパティからインスタンスを作成します。
