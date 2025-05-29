```
cellid(sim, name::Symbol, pos)
```

Returns the ID of the agent (node) from the raster `name` at the position `pos`. `pos` must be of type CartesianIndex or a Dims{N}.

See also [`add_raster!`](@ref), [`move_to!`](@ref), [`add_edge!`](@ref) and [`agentstate`](@ref)
