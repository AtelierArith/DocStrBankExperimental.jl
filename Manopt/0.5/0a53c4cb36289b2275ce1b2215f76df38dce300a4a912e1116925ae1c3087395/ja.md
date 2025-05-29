```
step_solver!(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, k)
```

[`AbstractManoptProblem`](@ref)`p`のために、[`AbstractManoptSolverState`](@ref) `ams`の値を修正することによって、1回の反復ステップ（`i`番目）を実行します。
