```
PauliZNoise(qind::Int, p::Real)
```

A frozen Pauli-Z noise channel acting on the qubit at index `qind` with noise strength `p`. Will damp X and Y Paulis equally by a factor of `1-p`. This corresponds to inserting a random Pauli Z operator into the circuit with probability `p/2`.
