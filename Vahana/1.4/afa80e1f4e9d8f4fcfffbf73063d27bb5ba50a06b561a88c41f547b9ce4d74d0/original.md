```
add_agent_per_process!(sim::Simulation, agent::T) where T
```

Add a single agent of type `T` to each process in the simulation. This function is designed to be used after initialization (when the simulation is distributed to the different processes in a parallel run) but outside of transition functions. It allows each process to have its own dedicated agent, useful for tasks like random agent selection or process-specific operations.

The function takes the simulation and the agent to be added as arguments. It returns the `AgentID` of the agent created on the current process.

!!! warning
    This function is not designed or optimized for adding many agents. Use it sparingly, typically to create a single agent per process for special purposes. For adding multiple agents, use the standard `add_agent!` or `add_agents!` functions within the appropriate simulation phases.


See also [`add_agent!`](@ref) and [`add_agents!`](@ref).
