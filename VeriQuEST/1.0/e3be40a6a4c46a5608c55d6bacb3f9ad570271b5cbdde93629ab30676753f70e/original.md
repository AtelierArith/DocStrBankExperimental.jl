```
create_resource(::MaliciousServer, client_graph, client_qureg, malicious_angles::Union{Float64,Vector{Float64}})
```

Creates a resource dictionary for a malicious server, including a cloned graph, a quantum environment, a quantum register, and a set of malicious angles.

# Arguments

  * `::MaliciousServer`: Indicates that this function is used in the context of a malicious server.
  * `client_graph::Graph`: The client's graph to be cloned.
  * `client_qureg::QuEST object`: The client's quantum register to be cloned.
  * `malicious_angles::Union{Float64,Vector{Float64}}`: The angles to be used for malicious behavior.

# Examples

```julia
client_graph = create_graph(Client(), 3)
client_qureg = create_qureg(Client(), 3)
malicious_angles = [π/4, π/2, 3π/4]
create_resource(MaliciousServer(), client_graph, client_qureg, malicious_angles)
```
