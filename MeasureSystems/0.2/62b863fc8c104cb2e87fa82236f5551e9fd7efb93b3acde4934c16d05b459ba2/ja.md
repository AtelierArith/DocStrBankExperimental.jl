```
μₑᵤ, μₚᵤ, μₚₑ, αinv, αG, ΩΛ
```

物理的に測定された無次元の`Coupling`値と不確かさは、電子と陽子の質量比`μₑᵤ`、陽子と原子質量比`μₚᵤ`、陽子と電子の質量比`μₚₑ`、逆微細構造定数`αinv`、および重力結合定数`αG`です。

```Julia
julia> μₑᵤ # electronunit(Universe)
μₑᵤ = 0.000548579909065(16)

julia> μₚᵤ # protonunit(Universe)
μₚᵤ = 1.007276466621(53)

julia> μₚₑ # protonelectron(Universe)
μₑᵤ⁻¹μₚᵤ = 1836.15267343(11)

julia> αinv # 1/finestructure(Universe)
α⁻¹ = 137.035999084(21)

julia> αG # coupling(Universe)
𝘩²𝘤⁻²R∞²α⁻⁴mP⁻²2² = 1.751810(39) × 10⁻⁴⁵

julia> ΩΛ # darkenergydensity(Universe)
ΩΛ = 0.6889(56)
```
