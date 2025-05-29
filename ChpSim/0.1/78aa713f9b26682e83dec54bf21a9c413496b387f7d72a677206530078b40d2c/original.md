```
ChpState(num_qubits[, bitpack=true])
```

The state of a quantum stabilizer circuit simulation.  I.e. the simulated state of a quantum computer after applying only Clifford operations to qubits that all start in the `|0⟩` state.

Supported operations: `cnot!`, `hadamard!`, `phase!`, `measure!`
