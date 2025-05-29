```
produce_initialised_graph(::Client, mg)
```

This function produces an initialised graph from a meta graph for a client in the MBQC model.  It simply creates a new graph from the meta graph.

# Arguments

  * `::Client`: The Client object.
  * `mg`: The MetaGraph to be converted into a graph.

# Returns

  * A new Graph created from the MetaGraph.

# Examples

```julia
client = Client()
mg = MetaGraphs.MetaGraph(graph)
produce_initialised_graph(client, mg)
```
