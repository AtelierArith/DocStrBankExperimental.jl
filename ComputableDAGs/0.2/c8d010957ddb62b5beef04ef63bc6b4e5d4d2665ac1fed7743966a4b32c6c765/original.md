```
optimize_step!(optimizer::AbstractOptimizer, graph::DAG)
```

Interface function that must be implemented by implementations of [`AbstractOptimizer`](@ref). Returns `true` if an operations has been applied, `false` if not, usually when a fixpoint of the algorithm has been reached.

It should do one smallest logical step on the given [`DAG`](@ref), muting the graph and, if necessary, the optimizer's state.
