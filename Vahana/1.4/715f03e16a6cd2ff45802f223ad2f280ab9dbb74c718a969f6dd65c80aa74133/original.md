```
connect_raster_neighbors!(sim, name::Symbol, edge_constructor; [distance::Int, metric:: Symbol, periodic::Bool])
```

All cells that are at most `distance` from each other (using the metric `metric`) are connected with edges, where the edges are created with the `edge_constructor`.

The `edge_constructor` must be a function with one argument with type Tuple{CartesianIndex, CartesianIndex}. The first CartesianIndex is the position of the source node, and the second CartesianIndex the position of the target node.

Valid metrics are :chebyshev, :euclidean and :manhatten.

The keyword periodic determines whether all dimensions are cyclic (e.g., in the two-dimensional case, the raster is a torus).

The default values of the optional keyword arguments are 1 for `distance`, :chebyshev for `metric` and true for `periodic`. which is equivalent to a Moore neighborhood. The :manhatten metric can be used to connect cells in the von Neumann neighborhood.

The agent types of agents created by the `agent_constructor` must be already registered via [`register_agenttype!`](@ref).

See also [`add_raster!`](@ref)
