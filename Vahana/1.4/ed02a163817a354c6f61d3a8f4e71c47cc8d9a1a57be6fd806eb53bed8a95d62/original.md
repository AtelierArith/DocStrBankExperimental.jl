```
write_agents(sim::Simulation, [types])
```

Writes the current agent state to the attached HDF5 file. If only the agents of a subset of agent types are to be written, this subset can be specified via the optional `types` argument.
