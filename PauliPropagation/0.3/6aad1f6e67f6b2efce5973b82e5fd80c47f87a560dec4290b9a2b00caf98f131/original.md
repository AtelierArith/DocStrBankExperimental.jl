```
PauliXNoise(qind::Int)
```

A Pauli-X noise channel acting on the qubit at index `qind`. Will damp Y and Z Paulis equally by a factor of `1-p`. This corresponds to inserting a random Pauli X operator into the circuit with probability `p/2`.
