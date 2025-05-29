Pauliチャネルデータ構造、主に[`StabMixture`](@ref)での使用を目的としています。

ユニタリPauliチャネルであることがわかっている場合、[`PauliChannel`](@ref)よりも便利に使用できます。

```jldoctest
julia> Tgate = UnitaryPauliChannel(
           (I, Z),
           ((1+exp(im*π/4))/2, (1-exp(im*π/4))/2)
       )
ユニタリPauliチャネルP = ∑ ϕᵢ Pᵢで、以下のブランチがあります：
with ϕᵢ | Pᵢ
 0.853553+0.353553im | + _
 0.146447-0.353553im | + Z

julia> PauliChannel(Tgate)
Pauliチャネルρ ↦ ∑ ϕᵢⱼ Pᵢ ρ Pⱼ†で、以下のブランチがあります：
with ϕᵢⱼ | Pᵢ | Pⱼ:
 0.853553+0.0im | + _ | + _
 0.0+0.353553im | + _ | + Z
 0.0-0.353553im | + Z | + _
 0.146447+0.0im | + Z | + Z
```
