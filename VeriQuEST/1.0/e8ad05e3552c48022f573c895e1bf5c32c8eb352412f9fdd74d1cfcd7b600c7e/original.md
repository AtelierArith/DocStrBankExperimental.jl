```
generate_property_graph!(::Client, round_type, resource::MBQCResourceState, state_type::Union{StateVector,DensityMatrix})
```

This function generates a property graph for a client in the MBQC model based on the round type.  It first creates a meta graph from the resource and adds the round type to it.  Then, it adds output qubits, sets the vertex type and IO qubits type, initializes the qubits,  adds flow vertices and correction vertices, initializes measurement outcomes,  and initializes the quantum state of the meta graph.  This function is run at the beginning of every round.

# Arguments

  * `::Client`: The Client object.
  * `round_type`: The round type.
  * `resource::MBQCResourceState`: The resource containing the graph and its coloring.
  * `state_type::Union{StateVector,DensityMatrix}`: The type of quantum state to create.

# Returns

  * The updated MetaGraph.

# Examples

```julia
client = Client()
resource = MBQCResourceState(graph)
round_type = "round1"
state_type = StateVector()
generate_property_graph!(client, round_type, resource, state_type)
```
