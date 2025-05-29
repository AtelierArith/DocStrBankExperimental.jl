```
make_time_mpo(H::MPOHamiltonian, dt::Number, alg) -> O::MPO
```

Construct an `MPO` that approximates $\exp(-iHdt)$.
