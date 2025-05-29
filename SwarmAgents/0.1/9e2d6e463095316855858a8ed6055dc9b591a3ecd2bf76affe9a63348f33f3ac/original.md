```
run_full_turn(agent::Agent, messages::AbstractVector{<:PT.AbstractMessage},
    context::Dict{Symbol, Any} = Dict{Symbol, Any}(); max_turns::Int = 5,
    kwargs...)
```

Runs a full turn of an agent (executes all tool calls).
