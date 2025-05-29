```
truncateweight(pstr::PauliStringType, max_weight::Real)
```

Return `true` if an integer Pauli string should be truncated because its weight (i.e., number of non-identity Paulis) is larger than `max_weight`. 
