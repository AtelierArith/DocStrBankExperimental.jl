```
function updateH!(sysenv::StateEnvs{ProjMPOSum2}, Hs::Vector{MPO}; recalcEnv::Bool = true)
```

Update Hamiltonian `H` in `sysenv::StateEnvs`. `recalcEnv = false` is not supported.
