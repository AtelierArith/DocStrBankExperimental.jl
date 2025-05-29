```
vahanasimplegraph(sim::Simulation; [agenttypes::Vector{DataType}, edgetypes::Vector{DataType}, show_ignorefrom_warning = true])
```

Creates a subgraph with nodes for all agents that have one of the `agenttypes` types, and all edges that have one of the `edgetypes` types and whose both adjacent node types are in `agenttypes`.

The default values for `agenttypes` and `edgetypes` are all registered agents/edgetypes (see [`register_agenttype!`](@ref) and [`register_edgetype!`](@ref)).

This subgraphs implements the AbstractSimpleGraph interface from the Graphs.jl package.

The edge types must not have the :IgnoreFrom property. If there are edge types with this property in the `edgetypes` vector, a warning will be displayed and these edges will be ignored. The warning can be suppressed by setting `show_ignorefrom_warning` to false.

!!! warning
    The AbstractGraph interface allows multiple edges between two nodes, but some function (e.g. those that convert the graph into a binary (sparse)matrix can produce undefined results for those graphs. So use this function with care.

