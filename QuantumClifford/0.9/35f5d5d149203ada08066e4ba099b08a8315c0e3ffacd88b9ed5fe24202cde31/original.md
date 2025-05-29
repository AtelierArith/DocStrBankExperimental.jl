A Pauli channel datastructure, mainly for use with [`StabMixture`](@ref).

More convenient to use than [`PauliChannel`](@ref) when you know your Pauli channel is unitary.

```jldoctest
julia> Tgate = UnitaryPauliChannel(
           (I, Z),
           ((1+exp(im*π/4))/2, (1-exp(im*π/4))/2)
       )
A unitary Pauli channel P = ∑ ϕᵢ Pᵢ with the following branches:
with ϕᵢ | Pᵢ
 0.853553+0.353553im | + _
 0.146447-0.353553im | + Z

julia> PauliChannel(Tgate)
Pauli channel ρ ↦ ∑ ϕᵢⱼ Pᵢ ρ Pⱼ† with the following branches:
with ϕᵢⱼ | Pᵢ | Pⱼ:
 0.853553+0.0im | + _ | + _
 0.0+0.353553im | + _ | + Z
 0.0-0.353553im | + Z | + _
 0.146447+0.0im | + Z | + Z
```
