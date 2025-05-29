```
stop_solver!(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, k)
```

現在の [`AbstractManoptProblem`](@ref) `amp`、ソルバーの現在の状態が格納されている [`AbstractManoptSolverState`](@ref) `ams`、および現在の反復 `i` に基づいて、この関数はソルバーを停止するかどうかを決定します。デフォルトでは、内部の [`StoppingCriterion`](@ref) `ams.stop` を呼び出すことを意味します。
