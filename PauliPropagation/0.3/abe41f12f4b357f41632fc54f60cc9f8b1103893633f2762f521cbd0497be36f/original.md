```
DepolarizingNoise(qind::Int, p::Real)
```

A frozen depolarizing noise channel acting on the qubit at index `qind` with noise strength `p`. Will damp X, Y, and Z Paulis equally by a factor of `1-p`.
