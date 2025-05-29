```
function StateEnvs(psi::MPS, H::MPO, Ms::Vector{MPS}; weight::Float64)
```

Constructor of the `StateEnvs` from a single `MPO` and a vector of `MPS` used for excited state DMRG.
