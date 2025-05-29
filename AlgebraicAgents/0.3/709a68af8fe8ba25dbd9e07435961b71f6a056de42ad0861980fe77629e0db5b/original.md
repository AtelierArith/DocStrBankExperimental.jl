```
run_graphviz(io::IO, graph::AbstractString; prog::Symbol=:dot, format::String="svg")
run_graphviz(path::AbstractString, graph::AbstractString; prog::Symbol=:dot, format::String="svg")
```

Run the Graphviz program to render the graph and stream the results into `io`. 

This requires either `prog` (e.g., `dot`) to be available in your path (see https://graphviz.org) or for the `Graphviz_jll` package to be installed and loaded before calling this function.

See [`wiring_diagram`](@ref) to obtain the Graphviz wiring diagram for an agent hierarchy.
