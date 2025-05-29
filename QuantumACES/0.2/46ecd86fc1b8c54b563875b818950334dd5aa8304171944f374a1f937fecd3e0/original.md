```
init_gate_probabilities(total_gates::Vector{Gate}, log_param::LognormalParameters)
```

Returns a dictionary of the Pauli error probabilities for each gate in `total_gates` generated according to the noise parameters `log_param`, ordered lexicographically following [`get_paulis`](@ref).
