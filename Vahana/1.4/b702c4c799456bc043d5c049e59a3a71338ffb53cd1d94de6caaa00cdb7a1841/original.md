```
num_agents(sim, ::Type{T}, [all_ranks=true])
```

If `all_ranks` is `true` this function retrieves the number of agents of type T of the simulation `sim`. When it is set to `false`, the function will return the number of agents managed by the process.

See also [`add_agents!`] and [`all_agents`](@ref).
