```
run_computation(::Client, ::MaliciousServer, server_resource, client_meta_graph, num_qubits_from_server, server_quantum_state)
```

Runs a quantum computation in the context of a client interacting with a malicious server. The computation involves updating phase angles, measuring along a specific basis, and storing the measurement outcomes.

# Arguments

  * `::Client`: Indicates that this function is used in the context of a client.
  * `::MaliciousServer`: Indicates that this function is used in the context of a malicious server.
  * `server_resource::Dict`: A dictionary containing server resources.
  * `client_meta_graph::Graph`: The client's meta graph.
  * `num_qubits_from_server::Int64`: The number of qubits received from the server.
  * `server_quantum_state::QuEST object`: The server's quantum state.

# Examples

```julia
server_resource = Dict("env" => create_quantum_env(Server()), "quantum_state" => create_qureg(Server(), 3), "graph" => create_graph(Server(), 3), "angles" => [π/4, π/2, 3π/4])
client_meta_graph = create_graph(Client(), 3)
num_qubits_from_server = 3
server_quantum_state = create_qureg(Server(), 3)
run_computation(Client(), MaliciousServer(), server_resource, client_meta_graph, num_qubits_from_server, server_quantum_state)
```
