```
run_verification(::Client, ::MaliciousServer, round_types, client_resource, state_type, malicious_angles)
```

Runs a verification process in the context of a client interacting with a malicious server. The process involves generating a property graph, initializing a graph and a quantum register, creating server resources, running a computation, and initializing a blank quantum state.

# Arguments

  * `::Client`: Indicates that this function is used in the context of a client.
  * `::MaliciousServer`: Indicates that this function is used in the context of a malicious server.
  * `round_types::Array`: An array of round types.
  * `client_resource::Dict`: A dictionary containing client resources.
  * `state_type::Symbol`: The type of the quantum state.
  * `malicious_angles::Union{Float64,Vector{Float64}}`: The angles to be used for malicious behavior.

# Examples

```julia
round_types = [:round1, :round2, :round3]
client_resource = Dict("env" => create_quantum_env(Client()), "quantum_state" => create_qureg(Client(), 3), "graph" => create_graph(Client(), 3))
state_type = :state1
malicious_angles = [π/4, π/2, 3π/4]
run_verification(Client(), MaliciousServer(), round_types, client_resource, state_type, malicious_angles)
```
