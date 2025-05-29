```
get_combined_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}}, gate_data::GateData)
```

Returns the combined gate probabilities obtained from the gate probabilities `gate_probabilities` by averaging SPAM noise parameters on each qubit, calculated using combined gate data `gate_data`.
