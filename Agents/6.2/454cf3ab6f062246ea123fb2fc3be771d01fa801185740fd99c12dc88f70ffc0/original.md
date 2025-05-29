```
GraphSpace(graph::AbstractGraph)
```

Create a `GraphSpace` instance that is underlined by an arbitrary graph from [Graphs.jl](https://github.com/JuliaGraphs/Graphs.jl). `GraphSpace` represents a space where each node (i.e. position) of a graph can hold an arbitrary amount of agents, and each agent can move between the nodes of the graph. The position type for this space is `Int`, use [`GraphAgent`](@ref) for convenience.

`GraphSpace` inherits from `DiscreteSpace` and all functions for [`DiscreteSpace`](@ref DiscreteSpace_exclusives) are available. On top of that, `Graphs.nv` and `Graphs.ne` can be used in a model with a `GraphSpace` to obtain the number of nodes or edges in the graph. The underlying graph can be altered using [`add_vertex!`](@ref) and [`rem_vertex!`](@ref).

An example using `GraphSpace` is [SIR model for the spread of COVID-19](@ref).

!!! note "Not for social networks!"
    `GraphSpace` is not intended for "social-network-like" agent based modelling, where each agent is equivalent with a node of a network/graph and the graph represents connections between agents. Rather, `GraphSpace` is suitable for when the coordinates of spatial locations are not as important as the connections between them. `GraphSpace` is suited for e.g., modelling cities where each can host many agents.

    If you want to make a "social-network" like simulation, see [the integration with Graphs.jl example](@ref social_networks). Typically you won't need a space structure at all!


## Distance specification

In functions like [`nearby_ids`](@ref), distance for `GraphSpace` means the degree of neighbors in the graph (thus distance is always an integer). For example, for `r=2` includes first and second degree neighbors. For 0 distance, the search occurs only on the origin node.

In functions like [`nearby_ids`](@ref) the keyword `neighbor_type=:default` can be used to select differing neighbors depending on the underlying graph directionality type.

  * `:default` returns neighbors of a vertex (position). If graph is directed, this is equivalent to `:out`. For undirected graphs, all options are equivalent to `:out`.
  * `:all` returns both `:in` and `:out` neighbors.
  * `:in` returns incoming vertex neighbors.
  * `:out` returns outgoing vertex neighbors.
