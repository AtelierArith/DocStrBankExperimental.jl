```
nearest_neighbor(agent, model::ABM{<:ContinuousSpace}, r) → nearest
```

Return the agent that has the closest distance to given `agent`. Return `nothing` if no agent is within distance `r`.
