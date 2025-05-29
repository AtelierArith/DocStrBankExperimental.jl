```
PauliString(nqubits::Int, pauli::Symbol, qind::Integer, coeff=1.0)
PauliString(nqubits::Int, paulis::Vector{Symbol}, qinds::Vector{Integer}, coeff=1.0)
```

Constructor for a `PauliString` on `nqubits` qubits from a `Symbol` (:I, :X, :Y, :Z) or `Vector{Symbol}`. Provide the index or indices for those symbols as `qind` or `qinds`. The coefficient of the Pauli string in the Pauli sum defaults to 1.0.
