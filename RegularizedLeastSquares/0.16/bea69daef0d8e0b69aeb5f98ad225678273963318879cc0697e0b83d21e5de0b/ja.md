```
SequentialState(states::Vector{ST}) where {S, ST <: AbstractSolverState{S}}
```

SequentialStateは、各アクティブな状態をイテレーションごとに順次実行するスケジューラです。
