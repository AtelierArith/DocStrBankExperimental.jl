```
getcoeff(psum::PauliSum, pstr::PauliString)
```

Get the coefficient of a `PauliString` in a `PauliSum`. Defaults to 0 if the Pauli string is not in the `PauliSum`. Requires that the integer Pauli string in `pstr` is the same type as the integer Pauli strings in `psum`.
