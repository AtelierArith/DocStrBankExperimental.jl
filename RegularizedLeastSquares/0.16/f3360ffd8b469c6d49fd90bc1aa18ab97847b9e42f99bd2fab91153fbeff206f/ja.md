```
MultiThreadingState(states::Vector{ST}) where {S, ST <: AbstractSolverState{S}}
```

MultiThreadingStateは、各アクティブな状態をイテレーションごとに並行して実行するスケジューラです。
