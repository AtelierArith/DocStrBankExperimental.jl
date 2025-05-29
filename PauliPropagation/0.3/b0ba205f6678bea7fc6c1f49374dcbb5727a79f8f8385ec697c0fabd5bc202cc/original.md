```
getcoeff(psum::PauliSum{PauliStringType,CoeffType}, pstr::PauliStringType)
```

Get the coefficient of an integer Pauli string in a `PauliSum`. Defaults to 0 if the Pauli string is not in the `PauliSum`. Requires that the integer Pauli string `pstr` is the same type as the integer Pauli strings in `psum`.
