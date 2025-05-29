```
function dmrg1(psi0::MPS, H::MPO, params::DMRGParams; kwargs...)
function dmrg1(psi0::MPS, H::CouplingModel, params::DMRGParams; kwargs...)
function dmrg1(psi0::MPS, Hs::Vector{MPO}, params::DMRGParams; kwargs...)
function dmrg1(psi0::MPS, H::MPO, Ms::Vector{MPS}, params::DMRGParams; kwargs...)
function dmrg1(psi0::MPS, Hs::Vector{MPO}, Ms::Vector{MPS}, params::DMRGParams; kwargs...)
function dmrg1(psi0::MPS, H::CouplingModel, Ms::Vector{MPS}, params::DMRGParams; kwargs...)
```

Performs single-site DMRG. All other details are same as in [`dmrg2`](@ref).
