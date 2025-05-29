```
getcoeff(psum::PauliSum, pstr::Vector{Symbol})
```

Get the coefficient of a Pauli string in a `PauliSum` by providing the Pauli string `pstr` as a vector of Symbols acting on all qubits.  This is consistent with how Pauli strings can be added to a `PauliSum` via `add!()`.  Defaults to 0 if the Pauli string is not in the `PauliSum`.
