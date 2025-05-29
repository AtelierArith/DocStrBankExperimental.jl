```
PlannerHeuristic(planner, [d_transform, s_transform])
```

Computes distance to the goal based on the solution returned by `planner`.

If an [`OrderedSolution`](@ref) is returned, the cost of solution is used as the heuristic estimate, (plus the heuristic value of final state, if the  planner is a [`ForwardPlanner`](@ref).)

If a [`PolicySolution`](@ref) is returned, the negated value (returned by [`get_value`](@ref)) is used as the heuristic estimate.

If `d_transform` or `s_transform` are provided, this transforms the input domain or state it is passed to the `planner`. This can be used to relax the  problem (e.g. by simplifying the domain, or adding / deleting predicates in the state).
