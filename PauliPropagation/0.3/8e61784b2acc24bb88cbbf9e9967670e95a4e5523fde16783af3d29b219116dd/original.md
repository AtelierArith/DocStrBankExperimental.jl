```
PauliZNoise(qind::Int)
```

A Pauli-Z noise channel acting on the qubit at index `qind`. Will damp X and Y Paulis equally by a factor of `1-p`. This corresponds to inserting a random Pauli Z operator with probability `p/2`.
