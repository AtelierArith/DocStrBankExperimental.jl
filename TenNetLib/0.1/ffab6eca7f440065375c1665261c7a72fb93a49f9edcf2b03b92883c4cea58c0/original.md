```
function updateH!(sysenv::StateEnvs{ProjCouplingModel_MPS}, H::CouplingModel, Ms::Vector{MPS};
                  weight::Float64, recalcEnv::Bool = true)
```

Update Hamiltonian `H` in `sysenv::StateEnvs`. `recalcEnv = false` is not supported.

  * `weight::Union{Nothing, Float64} = nothing`.
