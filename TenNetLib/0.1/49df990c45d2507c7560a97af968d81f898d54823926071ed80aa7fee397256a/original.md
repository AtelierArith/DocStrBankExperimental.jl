```
function StateEnvsTTN(psi::TTN, H::CouplingModel, Ms::Vector{TTN}; weight::Float64)
```

Constructor of StateEnvsTTN from a `CouplingModel` and a vector of TTN used for excited state search. Each terms in the `CouplingModel` are contracted in parallel.
