```
run_verification_simulator(::MaliciousServer, ::Terse, para, malicious_angles)
```

Runs a verification simulator in the context of a malicious server. The simulator involves defining colouring, computing backward flow, creating a graph resource, drawing random rounds, running verification, verifying rounds, and getting mode output.

# Arguments

  * `::MaliciousServer`: Indicates that this function is used in the context of a malicious server.
  * `::Terse`: Indicates that this function is used in a terse mode.
  * `para::Dict`: A dictionary containing parameters for the simulation.
  * `malicious_angles::Union{Float64,Vector{Float64}}`: The angles to be used for malicious behavior.

# Examples

```julia
para = Dict("input" => Dict("indices" => [1, 2, 3], "values" => [0.5, 0.5, 0.5]), "output" => [4, 5, 6], "graph" => create_graph(Client(), 3), "secret_angles" => [π/4, π/2, 3π/4], "forward_flow" => [0.1, 0.2, 0.3], "total_rounds" => 10, "computation_rounds" => 5, "state_type" => :state1)
malicious_angles = [π/4, π/2, 3π/4]
run_verification_simulator(MaliciousServer(), Terse(), para, malicious_angles)
```
