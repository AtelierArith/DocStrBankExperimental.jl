```
getcoeff(psum::PauliSum, pauli::Symbol, qind::Integer)
```

Get the coefficient of a Pauli string in a `PauliSum` by providing the Pauli string as a Symbol acting on qubit `qind`.  This is consistent with how Pauli strings can be added to a `PauliSum` via `add!()`.  Defaults to 0 if the Pauli string is not in the `PauliSum`.
