```
overlapbyorthogonality(pstr::PauliString, orthogonalfunc::Function)
```

Overlap a `PauliString` with a state or operator via function that returns true if the `PauliString` is orthogonal and hence has overlap 0.  An example `orthogonalfunc` is `containsXorY` which returns true if the `PauliString` contains an X or Y Pauli. If not orthogonal, then the overlap is the coefficient of the `PauliString`. This is particularly useful for overlaps with stabilizer states.
