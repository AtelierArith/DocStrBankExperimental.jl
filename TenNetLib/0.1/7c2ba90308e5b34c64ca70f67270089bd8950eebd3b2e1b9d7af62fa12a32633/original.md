```
function updateH!(engine::TDVPEngine, H::T;
                  recalcEnv::Bool = true) where T <: Union{MPO, Vector{MPO}, CouplingModel}
```

Update Hamiltonian `H` in `engine::TDVPEngine`. If `recalcEnv = false`, it reuses previous environments. `recalcEnv = false` is only defined when the `TDVPEngine` is created from a single `MPO`.
