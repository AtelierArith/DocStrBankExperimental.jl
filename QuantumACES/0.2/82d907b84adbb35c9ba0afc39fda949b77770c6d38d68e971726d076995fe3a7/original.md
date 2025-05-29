```
parse_qiskit_dict(counts::Dict{String, Int}, shots::Integer, qiskit_qubit_num::Integer; qiskit_qubit_map::Union{Vector{Int}, Nothing} = nothing)
```

Returns a parsed Stim-compatible matrix of `UInt8` circuit outcomes determined from the dictionary `counts` output by Qiskit with `shots` shots, where the circuit acts on `qiskit_qubit_num` qubits, and if `qiskit_qubit_map` is not `nothing`, checks that the measurement outcomes for the qubits not included in the map are 0.
