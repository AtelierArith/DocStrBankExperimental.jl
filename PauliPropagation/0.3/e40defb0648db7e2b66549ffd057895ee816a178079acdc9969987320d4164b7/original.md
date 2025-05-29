```
PauliXNoise(qind::Int, p::Real)
```

A frozen Pauli-X noise channel acting on the qubit at index `qind` with noise strength `p`. Will damp Y and Z Paulis equally by a factor of `1-p`. This corresponds to inserting a random Pauli X operator into the circuit with probability `p/2`.
