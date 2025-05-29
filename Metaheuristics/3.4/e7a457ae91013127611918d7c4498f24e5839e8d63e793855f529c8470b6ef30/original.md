```
termination_status_message(status)
```

Return a string of the message related to the `status`.

See [`TerminationStatusCode`](@ref)

### Example:

```julia-repl
julia> termination_status_message(Metaheuristics.ITERATION_LIMIT)
"Maximum number of iterations exceeded."

julia> termination_status_message(optimize(f, bounds))
"Maximum number of iterations exceeded."

julia> termination_status_message(ECA())
"Unknown stop reason."
```
