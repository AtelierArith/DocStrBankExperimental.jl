```
SplitOptimizer
```

An optimizer that simply applies an available [`NodeSplit`](@ref) on each step. It implements [`optimize_to_fixpoint!`](@ref). The fixpoint is reached when there are no more possible [`NodeSplit`](@ref)s in the graph.

See also: [`ReductionOptimizer`](@ref)
