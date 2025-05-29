```
get_marginal_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}})
get_marginal_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}}, gate_data::GateData)
```

Returns the marginal gate probabilities obtained from the gate probabilities `gate_probabilities` by marginalising error probabilities across the orbits of each of the gates.
