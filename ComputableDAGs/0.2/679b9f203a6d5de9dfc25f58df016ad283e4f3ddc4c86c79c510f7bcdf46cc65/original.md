```
fixpoint_reached(optimizer::AbstractOptimizer, graph::DAG)
```

Interface function that can be implemented by optimization algorithms that can reach a fixpoint, returning as a `Bool` whether it has been reached. The default implementation returns `false`.

See also: [`optimize_to_fixpoint!`](@ref)
