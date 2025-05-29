```
AmplitudeDampingNoise(qind::Int, gamma::Real)
```

A frozen amplitude damping noise channel acting on the qubit at index `qind` with noise strength `gamma`. Damps X and Y Paulis, and splits Z into and I and Z component (in the transposed Heisenberg picture).
