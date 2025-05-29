```
DephasingNoise(qind::Int)
DephasingNoise(qind::Int, p::Real)
```

This is an alias for `PauliZNoise`. A dephasing noise channel acting on the qubit at index `qind`. Will damp X and Y Paulis equally by a factor of `1-p`. If `p` is provided, this returns a frozen gate with that noise strength.
