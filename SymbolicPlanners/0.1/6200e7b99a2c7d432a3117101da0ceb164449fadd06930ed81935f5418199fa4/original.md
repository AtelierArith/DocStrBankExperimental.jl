```
PolicyValueHeuristic(policy::PolicySolution)
```

Wraps a `policy`, and returns the negated value estimate of a state  (provided by [`get_value`](@ref)) as the heuristic goal-distance estimate.
