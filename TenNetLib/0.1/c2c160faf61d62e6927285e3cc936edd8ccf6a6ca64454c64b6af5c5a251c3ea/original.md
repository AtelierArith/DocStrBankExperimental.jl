```
function StateEnvs(psi::MPS, H::CouplingModel, Ms::Vector{MPS}; weight::Float64)
```

Constructor of StateEnvs from a `CouplingModel` and a vector of MPS used for excited state DMRG. Each terms in the `CouplingModel` are contracted in parallel.
