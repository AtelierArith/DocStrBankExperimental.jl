```
overlapbyorthogonality(pstr::PauliString, orthogonalfunc::Function)
```

Overlap an integer Pauli string with a state or operator via function that returns true if the Pauli string is orthogonal and hence has overlap 0.  An example `orthogonalfunc` is `containsXorY` which returns true if the Pauli string contains an X or Y Pauli. If not orthogonal, then the overlap is 1. This is particularly useful for overlaps with stabilizer states.
