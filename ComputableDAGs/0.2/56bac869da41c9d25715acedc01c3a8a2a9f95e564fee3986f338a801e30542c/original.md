```
ReductionOptimizer
```

An optimizer that simply applies an available [`NodeReduction`](@ref) on each step. It implements [`optimize_to_fixpoint!`](@ref). The fixpoint is reached when there are no more possible [`NodeReduction`](@ref)s in the graph.

See also: [`SplitOptimizer`](@ref)
