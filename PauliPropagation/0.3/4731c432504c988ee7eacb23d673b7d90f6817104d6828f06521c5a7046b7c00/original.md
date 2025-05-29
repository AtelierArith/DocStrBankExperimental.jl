```
overlapbyorthogonality(psum::PauliSum, orthogonalfunc::Function)
```

Overlap a `PauliSum` with a state or operator via function that returns true if a Pauli string is orthogonal and hence doesn't contribute. An example `orthogonalfunc` is `containsXorY` which returns true if a Pauli string contains an X or Y Pauli. If not orthogonal, then a Pauli string contributes with its coefficient. This is particularly useful for overlaps with stabilizer states.
