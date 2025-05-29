```julia
mutable struct StabMixture{T, F}
```

混合 ∑ ϕᵢⱼ Pᵢ ρ Pⱼ† を表し、ここで ρ は純粋な安定化子状態です。

```jldoctest
julia> StabMixture(S"-X")
混合 ∑ ϕᵢⱼ Pᵢ ρ Pⱼ† で、ここで ρ は
𝒟ℯ𝓈𝓉𝒶𝒷
+ Z
𝒮𝓉𝒶𝒷
- X
であり、ϕᵢⱼ | Pᵢ | Pⱼ:
 1.0+0.0im | + _ | + _

julia> pcT
ユニタリーパウリチャネル P = ∑ ϕᵢ Pᵢ で、以下のブランチがあります:
ϕᵢ | Pᵢ
 0.853553+0.353553im | + _
 0.146447-0.353553im | + Z

julia> apply!(StabMixture(S"-X"), pcT)
混合 ∑ ϕᵢⱼ Pᵢ ρ Pⱼ† で、ここで ρ は
𝒟ℯ𝓈𝓉𝒶𝒷
+ Z
𝒮𝓉𝒶𝒷
- X
であり、ϕᵢⱼ | Pᵢ | Pⱼ:
 0.0+0.353553im | + _ | + Z
 0.0-0.353553im | + Z | + _
 0.853553+0.0im | + _ | + _
 0.146447+0.0im | + Z | + Z
```

参照: [`PauliChannel`](@ref)
