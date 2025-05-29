```
run_computation(client_meta_graph, num_qubits_from_server, server_quantum_state)
```

Runs a computation by creating a new `Client` instance for each qubit from the server. The function iterates over the number of qubits from the server, updates the client's ϕ, measures along the ϕ basis on the client, updates the measurement on the client, and stores the measurement outcome on the client. The updated client meta graph is returned.

# Arguments

  * `client_meta_graph`: The client's meta graph.
  * `num_qubits_from_server`: The number of qubits from the server.
  * `server_quantum_state`: The quantum state of the server.

# Returns

  * `client_meta_graph`: The updated client meta graph.

# Examples

```julia
client_meta_graph = create_graph(Client(), 3)
num_qubits_from_server = 3
server_quantum_state = create_quantum_state(Client(), num_qubits_from_server)
updated_client_meta_graph = run_computation(client_meta_graph, num_qubits_from_server, server_quantum_state)
```
