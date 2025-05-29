```
function updateH!(sysenv::StateEnvs{ProjMPO}, H::MPO; recalcEnv::Bool = true)
```

Update Hamiltonian `H` in `sysenv::StateEnvs`. If `recalcEnv = false`, it reuses previous environments.
