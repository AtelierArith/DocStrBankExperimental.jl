```
SequentialState(states::Vector{ST}) where {S, ST <: AbstractSolverState{S}}
```

SequentialState is a scheduler that runs each active state sequentially per iteration.
