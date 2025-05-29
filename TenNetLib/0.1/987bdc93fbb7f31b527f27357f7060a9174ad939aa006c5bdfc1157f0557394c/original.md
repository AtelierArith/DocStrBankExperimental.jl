```
function updateH!(engine::TDVPEngine, H::T, Ms::Vector{MPS};
                  weight::Float64,
                  recalcEnv::Bool = true) where T <: Union{MPO, Vector{MPO}, CouplingModel}
```

Update Hamiltonian `H` in `engine::TDVPEngine`. `recalcEnv = false` is not supported.
