```
get_average_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}})
get_average_gate_probabilities(gate_probabilities::Dict{Gate, Vector{Float64}}, gate_data::GateData)
```

Returns the averaged gate probabilities obtained from the gate probabilities `gate_probabilities` by averaging error probabilities within the orbits of each of the gates.
