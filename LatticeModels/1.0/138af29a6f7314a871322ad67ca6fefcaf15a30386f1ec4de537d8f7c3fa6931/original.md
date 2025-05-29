```
localexpect(op, state)
```

Compute the expectation values of the operator `op` acting on the local Hilbert space of `state`. The result is a `LatticeValue` with the same lattice as the input state.

## Arguments

  * `op`: A `DataOperator` representing the operator.
  * `state`: A `Ket` or `Bra` representing the wavefunction or an `Operator` representing the density matrix.
