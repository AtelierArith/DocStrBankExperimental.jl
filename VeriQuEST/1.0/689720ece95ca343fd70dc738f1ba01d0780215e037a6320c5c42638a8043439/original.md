```
create_quantum_state(::Server,::DensityMatrix,quantum_env,num_qubits)
```

Creates a new quantum state in the context of a server.

# Arguments

  * `::Server`: Indicates that this function is used in the context of a server.
  * `::DensityMatrix`: Indicates that the quantum state is a density matrix.
  * `quantum_env`: The QuEST environment in which the quantum state is created.
  * `num_qubits`: The number of qubits in the quantum state.

# Examples

```julia
create_quantum_state(Server(),DensityMatrix(),quantum_env,num_qubits)
```
