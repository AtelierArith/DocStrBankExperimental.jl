```
AmplitudeDampingNoise(qind::Int)
```

An amplitude damping noise channel acting on the qubit at index `qind`. Damps X and Y Paulis by a factor of sqrt(1-gamma) and splits Z into and gamma * I and (1-gamma) * Z component (in the transposed Heisenberg picture).
