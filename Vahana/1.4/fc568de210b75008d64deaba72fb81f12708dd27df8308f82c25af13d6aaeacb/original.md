```
vahanagraph(sim::Simulation; [agenttypes::Vector{DataType}, edgetypes::Vector{DataType}, show_ignorefrom_warning = true, drop_multiedges = false])
```

Creates a subgraph with nodes for all agents that have one of the `agenttypes` types, and all edges that have one of the `edgetypes` types and whose both adjacent agents have are of a type in `agenttypes`.

The default values for `agenttypes` and `edgetypes` are all registered agents/edgetypes (see [`register_agenttype!`](@ref) and [`register_edgetype!`](@ref)).

This subgraphs implements the AbstractGraph interface from the Graphs.jl package, so that e.g. GraphMakie can be used to visualize the subgraph. See also [`create_graphplot`](@ref).

The AbstractGraph interface allows multiple edges between two nodes, but some functions (e.g. those that convert the graph to a binary (sparse) matrix) may produce undefined results for these graphs, e.g. when graphplot is called from GraphMakie.jl. If the keyword `drop_multiedges` is true and there are multiple edges, only the edge of the type that is first in the edgetypes vector is added to the generated graph.

The edge types must not have the :IgnoreFrom property. If there are edge types with this property in the `edgetypes` vector, a warning will be displayed and these edges will be ignored. The warning can be suppressed by setting `show_ignorefrom_warning` to false.
