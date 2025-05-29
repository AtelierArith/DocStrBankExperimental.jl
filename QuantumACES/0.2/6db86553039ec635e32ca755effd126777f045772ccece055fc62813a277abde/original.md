```
get_stim_circuit(c::AbstractCircuit)
get_stim_circuit(c::AbstractCircuit, circuit_tuple::Vector{Int})
get_stim_circuit(c::AbstractCircuit, gate_probabilities::Dict{Gate, Vector{Float64}})
get_stim_circuit(c::AbstractCircuit, circuit_tuple::Vector{Int}, gate_probabilities::Dict{Gate, Vector{Float64}})
get_stim_circuit(d::Design)
get_stim_circuit(d::Design, gate_probabilities::Dict{Gate, Vector{Float64}})
get_stim_circuit(d_rand::RandDesign)
get_stim_circuit(d_rand::RandDesign, gate_probabilities::Dict{Gate, Vector{Float64}})
```

Returns the Stim circuit for the circuit `c`, stored in the design `d`, or randomised design `d_rand`, optionally applying the tuple `circuit_tuple` with the gate probabilities `gate_probabilities`.
