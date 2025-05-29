```
produce_initialised_qureg(client::Client, mg)
```

This function retrieves the quantum state from a meta graph for a client in the MBQC model.  It uses the `get_prop` function to get the `:quantum_state` property from the meta graph.

# Arguments

  * `client::Client`: The Client object.
  * `mg`: The MetaGraph from which the quantum state will be retrieved.

# Returns

  * The quantum state of the MetaGraph.

# Examples

```julia
client = Client()
mg = MetaGraphs.MetaGraph(graph)
produce_initialised_qureg(client, mg)
```
