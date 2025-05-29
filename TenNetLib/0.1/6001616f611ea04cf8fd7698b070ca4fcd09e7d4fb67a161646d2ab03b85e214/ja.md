```
function dmrg1(psi0::MPS, H::MPO, params::DMRGParams; kwargs...)
function dmrg1(psi0::MPS, H::CouplingModel, params::DMRGParams; kwargs...)
function dmrg1(psi0::MPS, Hs::Vector{MPO}, params::DMRGParams; kwargs...)
function dmrg1(psi0::MPS, H::MPO, Ms::Vector{MPS}, params::DMRGParams; kwargs...)
function dmrg1(psi0::MPS, Hs::Vector{MPO}, Ms::Vector{MPS}, params::DMRGParams; kwargs...)
function dmrg1(psi0::MPS, H::CouplingModel, Ms::Vector{MPS}, params::DMRGParams; kwargs...)
```

単一サイトDMRGを実行します。他の詳細は[`dmrg2`](@ref)と同じです。
