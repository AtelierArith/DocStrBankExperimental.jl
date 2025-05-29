```
optimize_to_fixpoint!(optimizer::AbstractOptimizer, graph::DAG)
```

Interface function that can be implemented by optimization algorithms that can reach a fixpoint. The algorithm will be run until that fixpoint is reached, at which point [`fixpoint_reached`](@ref) should return true.

A usual implementation might look like this:

```julia
    function optimize_to_fixpoint!(optimizer::MyOptimizer, graph::DAG)
        while !fixpoint_reached(optimizer, graph)
            optimize_step!(optimizer, graph)
        end
        return nothing
    end
```
