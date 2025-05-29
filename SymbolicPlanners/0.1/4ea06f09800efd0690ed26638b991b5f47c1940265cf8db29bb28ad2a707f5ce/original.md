```
ReachabilityHeuristic(max_steps::Int=100)
```

Heuristic which performs a reachability analysis for the goal via abstract interpretation, returning an optimistic estimate of the number or cost of the actions required to reach the goal, or `Inf` if the goal is not reached within `max_steps` of abstract action execution.

For propositional domains (i.e. domains with no non-Boolean fluents), this returns the same value as [`HMax`](@ref). For domains with numeric fluents or other datatypes, this provides more informed estimates by performing abstract interpretation of operations on those datatypes (e.g. interval arithmetic).
