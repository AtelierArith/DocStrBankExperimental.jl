```
get_stim_circuit(circuit::Vector{Layer}, gate_probabilities::Dict{Gate, Vector{Float64}}, noisy_prep::Bool, noisy_meas::Bool; extra_fields::Dict{Symbol, Any} = Dict{Symbol, Any}(), meas_and_reset::Bool = false)
```

Returns a Stim string representation of the circuit `circuit` alongside error probabilities specified by `gate_probabilities`, as well as noisy preparations if `noisy_prep` is `true` and noisy measurements if `noisy_meas` is `true`. Qubit coordinates are specified by `extra_fields` if it contains a [`CodeParameters`](@ref) object. Reset types are specified by `reset_type` and can be `:reset`, `:meas`, or `:meas_reset`.

Stim orders one-qubit Paulis as: X, Y, Z. We order one-qubit Paulis as: X, Z, Y. The indexing to transform between these orderings is: 1, 3, 2.

Stim orders two-qubit Paulis as: IX, IY, IZ, XI, XX, XY, XZ, YI, YX, YY, YZ, ZI, ZX, ZY, ZZ. We order two-qubit Paulis as: XI, IX, XX, ZI, YI, ZX, YX, IZ, XZ, IY, XY, ZZ, YZ, ZY, YY. The indexing to transform from the Stim ordering to ours is: 4, 1, 5, 12, 8, 13, 9, 3, 7, 2, 6, 15, 11, 14, 10. The indexing to transform from our ordering to the Stim ordering is: 2, 10, 8, 1, 3, 11, 9, 5, 7, 15, 13, 4, 6, 14, 12.
