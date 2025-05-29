```
store_measurement_outcome!(client::Client, client_meta_graph, qubit, outcome)
```

This function stores the measurement outcome of a specific qubit in the client's meta graph.  It uses the `set_p` function to set the property in the meta graph.

# Arguments

  * `client::Client`: The Client object.
  * `client_meta_graph`: The MetaGraph where the measurement outcome will be stored.
  * `qubit`: The qubit whose measurement outcome is being stored.
  * `outcome`: The measurement outcome to be stored.

# Returns

  * Nothing. The function modifies the client*meta*graph in-place.

# Examples

```julia
client = Client()
client_meta_graph = MetaGraphs.MetaGraph(graph)
qubit = 1
outcome = 0
store_measurement_outcome!(client, client_meta_graph, qubit, outcome)
```
