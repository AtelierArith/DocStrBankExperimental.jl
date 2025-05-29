```
add!(psum::PauliSum, pstr::PauliString)
```

Add a `PauliString` `pstr` to a `PauliSum` `psum`. Changes `psum` in-place. `psum` and `pstr` need to be defined on the same number of qubits and have the same coefficient type.
