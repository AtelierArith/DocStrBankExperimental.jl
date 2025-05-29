```
MultiThreadingState(states::Vector{ST}) where {S, ST <: AbstractSolverState{S}}
```

MultiThreadingState is a scheduler that runs each active state in parallel per iteration.
