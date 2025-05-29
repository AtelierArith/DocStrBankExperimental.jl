```
DataFrame(sim::Simulation, T::DataType; types = false, localnr = false)
```

Creates a DataFrame with the current state of agents or edges of type `T`.  By default, the ID columns show the complete [`AgentID`](@ref). for readability (and the use of [`show_agent`](@ref)) it may be useful to show only the lowest 36 bits, which gives a much more readable value, by setting the `localnr` argument to true. Since for edges the type information of the source and target agents is no longer available in this case, the `types` argument can be used to create additional columns containing the types of these agents.

!!! info
    `DataFrame` is only available when the DataFrame.jl package is imported by the model implementation.


!!! warning
    In parallel simulations, the `DataFrame` method converts only the local graph partition (agents or edges) residing on the current MPI rank. It does not provide a global view of the entire distributed graph. To obtain a complete list of all agent states across all ranks, use the [`all_agents`](@ref) function. Similarly, for edges, use the [`all_edges`](@ref) function to get a global view of all edges in the distributed graph.

