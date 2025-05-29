```julia
mutable struct StabMixture{T, F}
```

Represents mixture ∑ ϕᵢⱼ Pᵢ ρ Pⱼ† where ρ is a pure stabilizer state.

```jldoctest
julia> StabMixture(S"-X")
A mixture ∑ ϕᵢⱼ Pᵢ ρ Pⱼ† where ρ is
𝒟ℯ𝓈𝓉𝒶𝒷
+ Z
𝒮𝓉𝒶𝒷
- X
with ϕᵢⱼ | Pᵢ | Pⱼ:
 1.0+0.0im | + _ | + _

julia> pcT
A unitary Pauli channel P = ∑ ϕᵢ Pᵢ with the following branches:
with ϕᵢ | Pᵢ
 0.853553+0.353553im | + _
 0.146447-0.353553im | + Z

julia> apply!(StabMixture(S"-X"), pcT)
A mixture ∑ ϕᵢⱼ Pᵢ ρ Pⱼ† where ρ is
𝒟ℯ𝓈𝓉𝒶𝒷
+ Z
𝒮𝓉𝒶𝒷
- X
with ϕᵢⱼ | Pᵢ | Pⱼ:
 0.0+0.353553im | + _ | + Z
 0.0-0.353553im | + Z | + _
 0.853553+0.0im | + _ | + _
 0.146447+0.0im | + Z | + Z
```

See also: [`PauliChannel`](@ref)
