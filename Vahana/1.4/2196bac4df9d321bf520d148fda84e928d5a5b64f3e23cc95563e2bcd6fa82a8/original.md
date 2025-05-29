```
add_raster!(sim, name::Symbol, dims::NTuple{N, Int}, agent_constructor)
```

Adds a n-dimensional grid to `sim`, with the dimensions `dims`.

For each cell a new node/agent is added to the graph. To create the agent, the `agent_constructor` function is called, with the cell position in form of an `CartesianIndex` as argument.

The symbol `name` is an identifier for the created raster, as it is allowed to add multiple rasters to `sim`. 

The types of the agents created by the `agent_constructor` must be already registered via [`register_agenttype!`](@ref).

Returns a vector with the IDs of the created agents.

Can be only called before [`finish_init!`](@ref).

See also [`calc_raster`](@ref) [`connect_raster_neighbors!`](@ref) and [`move_to!`](@ref).
