```julia
ModifyHamiltonianField!(Ham::Hamiltonian, uc::UnitCell, newFields::Vector{Float64} ; dim::Int64=4, verbose::Bool=false)
```

Faster implementation of modifying ONLY the on-site field part of a `Hamiltonian`. `newFields` must be a vector of the same length as `uc.basis`. `dim` is an optional argument which determines which element of on-site field is being replaced.
