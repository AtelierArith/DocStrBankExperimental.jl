```
add!(psum::PauliSum, pauli::Symbol, qind::Integer, coeff=1.0)
add!(psum::PauliSum, paulis::Vector{Symbol}, qinds::Vector{Integer}, coeff=1.0)
```

Add a Pauli string to a `PauliSum` `psum`. Changes `psum` in-place. Provide the Pauli string as a `Symbol` (:I, :X, :Y, :Z) or `Vector{Symbol}`. Provide the index or indices for those symbols as `qind` or `qinds`. The coefficient of the Pauli string in the Pauli sum defaults to 1.0.
