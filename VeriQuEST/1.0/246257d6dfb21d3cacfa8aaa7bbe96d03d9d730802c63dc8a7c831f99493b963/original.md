```
initialise_quantum_state_meta_graph!(mbqc::MBQC, client::Client, state_type::Union{StateVector,DensityMatrix}, mg)
```

This function initializes the quantum state of a meta graph for a client in the MBQC model.  It first creates a quantum environment and a quantum state of the specified type.  Then, for each vertex in the meta graph, it gets the vertex type and vertex IO type,  and uses these to initialize the qubit in the quantum state.  Finally, it sets the quantum state as a property of the meta graph.

# Arguments

  * `::MBQC`: The MBQC object.
  * `::Client`: The Client object.
  * `state_type::Union{StateVector,DensityMatrix}`: The type of quantum state to create.
  * `mg`: The MetaGraph to which the properties will be added.

# Returns

  * The updated MetaGraph.

# Examples

```julia
mbqc = MBQC()
client = Client()
mg = MetaGraphs.MetaGraph(graph)
state_type = StateVector()
initialise_quantum_state_meta_graph!(mbqc, client, state_type, mg)
```
