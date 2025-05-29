```
get_full_average_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}})
get_full_average_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}}, gate_data::GateData)
```

Returns the fully averaged gate probabilities obtained from the gate probabilities `gate_probabilities` by averaging all error probabilities within each of the gates.
