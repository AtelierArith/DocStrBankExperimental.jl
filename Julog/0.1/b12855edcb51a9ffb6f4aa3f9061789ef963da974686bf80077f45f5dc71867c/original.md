```
derive(goals, clauses; <keyword arguments>)
fwd_chain(goals, clauses; <keyword arguments>)
```

Derive goals via forward-chaining from the initial set of clauses.

# Arguments

  * `goals::Vector{<:Term}`: A list of Julog terms to be prove or query.
  * `clauses::Vector{Clause}`: A list of Julog clauses.
  * `max-steps::Real=100`: Maximum steps before terminating with failure.

See `resolve` for other supported arguments.
