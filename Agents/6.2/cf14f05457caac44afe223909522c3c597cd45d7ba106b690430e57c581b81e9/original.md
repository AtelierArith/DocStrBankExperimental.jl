```
add_agent_single!(agent, model::ABM{<:DiscreteSpace}) → agent
```

Add the `agent` to a random position in the space while respecting a maximum of one agent per position, updating the agent's position to the new one.

This function does nothing if there aren't any empty positions.
