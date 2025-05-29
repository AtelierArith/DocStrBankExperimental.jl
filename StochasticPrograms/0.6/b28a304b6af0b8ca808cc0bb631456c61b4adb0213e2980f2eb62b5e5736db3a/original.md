```
all_constraints(stochasticprogram::StochasticProgram, stage::Integer, function_type, set_type)::Vector{<:SPConstraintRef}
```

Return a list of all decision constraints currently in the `stochasticprogram` at `stage` where the function has type `function_type` and the set has type `set_type`. The constraints are ordered by creation time. This errors if regular constraints are queried. If so, either annotate the relevant variables with [`@decision`](@ref) or first query the relevant JuMP subproblem and use the regular `all_constraints` function.
