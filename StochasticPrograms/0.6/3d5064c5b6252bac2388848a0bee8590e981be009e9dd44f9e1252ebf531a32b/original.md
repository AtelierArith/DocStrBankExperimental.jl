```
num_constraints(stochasticprogram::StochasticProgram{N}, stage::Integer, function_type, set_type)::Int64
```

Return the number of decision constraints currently in the `stochasticprogram` at `stage` where the function has type `function_type` and the set has type `set_type`. This errors if regular constraints are queried. If so, either annotate the relevant variables with [`@decision`](@ref) or first query the relevant JuMP subproblem and use the regular `all_constraints` function.
