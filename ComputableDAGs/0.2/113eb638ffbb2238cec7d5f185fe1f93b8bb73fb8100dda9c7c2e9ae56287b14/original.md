```
optimize!(optimizer::AbstractOptimizer, graph::DAG, n::Int)
```

Function calling the given optimizer `n` times, muting the graph. Returns `true` if the requested number of operations has been applied, `false` if not, usually when a fixpoint of the algorithm has been reached.

If a more efficient method exists, this can be overloaded for a specific optimizer.
