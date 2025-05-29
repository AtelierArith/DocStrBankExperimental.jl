```
expect(p::PauliOperator, st::AbstractStabilizer)
```

Compute the expectation value of a Pauli operator `p` on a stabilizer state `st`. This function will allocate a temporary copy of the stabilizer state `st`.
