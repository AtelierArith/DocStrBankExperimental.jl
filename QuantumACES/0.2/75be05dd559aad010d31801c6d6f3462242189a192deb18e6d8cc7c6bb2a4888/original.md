```
get_stim_memory_circuit(c::AbstractCircuit, gate_probabilities::Dict{Gate, Vector{Float64}}, memory_type::Symbol, rounds::Integer; reset_type::Symbol = :meas_reset)
get_stim_memory_circuit(c::AbstractCircuit, memory_type::Symbol, rounds::Integer; reset_type::Symbol = :meas_reset)
```

Returns a Stim string representation of the memory circuit corresponding to the syndrome extraction circuit `c`, optionally using the gate error probabilities `gate_probabilities`, memory type `memory_type`, which can be either `:x` or `:z`, number of rounds `rounds`, and reset type `reset_type`, which can be either `:meas_reset` or `:meas`.

If you want to add support for custom syndrome extraction circuits `c` which do not store their code parameters in the [`CodeParameters`](@ref) object, you will need to define new methods for `get_stim_qubits`, `get_stim_initialise`, `get_stim_detectors`, and `get_stim_measure_detectors` to make this function work.
