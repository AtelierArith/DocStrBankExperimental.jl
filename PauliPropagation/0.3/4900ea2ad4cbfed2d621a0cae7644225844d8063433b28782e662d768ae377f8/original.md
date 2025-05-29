```
PauliYNoise(qind::Int, p::Real)
```

A frozen Pauli-Y noise channel acting on the qubit at index `qind` with noise strength `p`. Will damp X and Z Paulis equally by a factor of `1-p`. This corresponds to inserting a random Pauli Y operator into the circuit with probability `p/2`.
