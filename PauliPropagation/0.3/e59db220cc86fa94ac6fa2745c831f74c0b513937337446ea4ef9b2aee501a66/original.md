```
clifford_map
```

Global dictionary of Clifford gates and their action on Pauli strings. Currently supported Clifford gates are `:H`, `:X`, `:Y`, `:Z`, `:SX`, `:SY`, `:S` (`:SZ`) , `:CNOT`, `:CZ`, :ZZpihalf`, and`:SWAP`. If one indexes into the returned arrays with the integer that corresponds to the partial Pauli string, the returned tuple is`(sign, partial*pstr)`where`sign`is the sign change and`partial*pstr` is the new partial Pauli string.
