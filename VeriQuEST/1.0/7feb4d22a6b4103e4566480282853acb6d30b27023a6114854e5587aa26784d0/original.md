```
add_round_type!(::Client, mg, round_type)
```

This function adds a round type to the meta graph for a client in the MBQC model.  It sets the `:round_type` property of the meta graph to the specified round type.

# Arguments

  * `::Client`: The Client object.
  * `mg`: The MetaGraph to which the property will be added.
  * `round_type`: The round type to be added to the meta graph.

# Returns

  * The updated MetaGraph.

# Examples

```julia
client = Client()
mg = MetaGraphs.MetaGraph(graph)
round_type = "round1"
add_round_type!(client, mg, round_type)
```
