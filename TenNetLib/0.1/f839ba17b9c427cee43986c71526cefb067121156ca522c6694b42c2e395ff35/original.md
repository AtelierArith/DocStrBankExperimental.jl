```
function StateEnvs(psi::MPS, Hs::Vector{MPO}, Ms::Vector{MPS}; weight::Float64)
```

Constructor of the `StateEnvs` from a vector of `MPO` and a vector of `MPS` used for excited state DMRG. Environments for `MPO`s are contracted in parallel.
