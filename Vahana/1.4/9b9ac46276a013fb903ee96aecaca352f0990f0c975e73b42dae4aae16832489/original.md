```
move_to!(sim, name::Symbol, id::AgentID, pos, edge_from_raster, edge_to_raster; [distance = 0, metric = :chebyshev, periodic = true])
```

Creates up to two edges of type between the agent with ID `id` and the cell from the raster `name` at the position `pos`.

`pos` must be of type CartesianIndex or a Dims{N}. 

`edge_from_raster` is the edge that will be added with the cell as source node and the agent as target node. `edge_from_raster` can be `nothing`, in this case no edge will be added with the agent as target node.

`edge_to_raster` is the edge that will be added with the agent as source node and the cell as target node. `edge_to_raster` can be `nothing`, in this case no edge will be added with the agent as source node.

Using the keyword arguments, it is possible to add additional edges to the surroundings of the cell at position `pos` in the same raster, i.e. to all cells at distance `distance` under metric `metric`, where valid metrics are `:chebyshev`, `:euclidean` and `:manhatten`. And the keyword `periodic` determines whether all dimensions are cyclic.

When the `only_surrounding` keyword is set to true, only edges to the surroundings cells of `pos` will be created, not to the cell at position `pos` itself.

See also [`add_raster!`](@ref) and [`connect_raster_neighbors!`](@ref) 
