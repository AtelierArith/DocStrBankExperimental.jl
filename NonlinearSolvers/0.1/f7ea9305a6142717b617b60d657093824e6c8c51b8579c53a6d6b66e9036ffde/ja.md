```
solve!(
    method::AbstractNonlinearSolverMethod{FT},
    soltype::SolutionType = CompactSolution(),
    tol::Union{Nothing, AbstractTolerance} = nothing,
    maxiters::Union{Nothing, Int} = 10_000,
)
```

非線形システムを解く

  * `method` 数値的手法
  * `soltype` 解のタイプ（`CompactSolution` または `VerboseSolution`）
  * `tol` 停止許容誤差
  * `maxiters` 実行する最大反復回数
