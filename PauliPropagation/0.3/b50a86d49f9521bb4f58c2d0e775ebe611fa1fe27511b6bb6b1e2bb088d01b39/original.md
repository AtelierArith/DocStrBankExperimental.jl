```
PauliYNoise(qind::Int)
```

A Pauli-Y noise channel acting on the qubit at index `qind`. Will damp X and Z Paulis equally by a factor of `1-p`. This corresponds to inserting a random Pauli Y operator into the circuit with probability `p/2`.
