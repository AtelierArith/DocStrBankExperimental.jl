```
GoalDependentPolicyHeuristic(policies::Dict, [default])
```

Wraps a dictionary mapping planning [`Specification`](@ref)s to  [`PolicySolution`](@ref)s. Given a particular specification, the heuristic looks up the corresponding policy and returns its negated estimate of a state's value as the heuristic goal-distance estimate.

If a `default` is provided, then this is used to construct a new policy `policy = default(domain, state, spec)` for a specification `spec` that is not found in the dictionary. Otherwise, an error is thrown.
