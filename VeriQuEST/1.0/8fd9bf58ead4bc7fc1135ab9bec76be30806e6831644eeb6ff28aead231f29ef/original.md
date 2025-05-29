```
update_ϕ!(::MBQC, ::ComputationQubit, qT::Union{NoInputQubits,InputQubits}, meta_graph, vertex)
```

Updates the ϕ value of a given vertex in the `meta_graph` during a computation round in a Measurement-Based Quantum Computing (MBQC) model with a computation qubit and either no input qubits or input qubits. The new ϕ value is computed based on several properties of the vertex including its secret angle, X correction, and Z correction.

# Arguments

  * `::MBQC`: Indicates that this function is used in the MBQC model.
  * `::ComputationQubit`: Indicates that a computation qubit is used.
  * `qT::Union{NoInputQubits,InputQubits}`: Indicates that either no input qubits or input qubits are used.
  * `meta_graph`: The graph to be updated.
  * `vertex`: The vertex in the graph for which the ϕ value is to be updated.

# Returns

  * The updated `meta_graph`.

# Examples

```julia
updated_graph = update_ϕ!(MBQC(), ComputationQubit(), NoInputQubits(), meta_graph, vertex) # Updates the ϕ value of the specified vertex in the graph
updated_graph = update_ϕ!(MBQC(), ComputationQubit(), InputQubits(), meta_graph, vertex) # Updates the ϕ value of the specified vertex in the graph
```
