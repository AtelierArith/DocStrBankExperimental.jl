```
init!(solver::AbstractLinearSolver, state::AbstractSolverState, b::AbstractMatrix; scheduler = SequentialState, kwargs...)
```

`scheduler`に対応する状態を渡し、`b`の各列でソルバーを初期化します。
