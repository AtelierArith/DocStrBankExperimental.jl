```
move_agent_single!(agent, model::ABM{<:DiscreteSpace}; cutoff) → agent
```

Move agent to a random position while respecting a maximum of one agent per position. If there are no empty positions, the agent won't move.

The keyword `cutoff = 0.998` is sent to [`random_empty`](@ref).
