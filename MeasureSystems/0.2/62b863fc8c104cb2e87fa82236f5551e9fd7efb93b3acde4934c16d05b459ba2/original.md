```
μₑᵤ, μₚᵤ, μₚₑ, αinv, αG, ΩΛ
```

Physical measured dimensionless `Coupling` values with uncertainty are the electron to proton mass ratio `μₑᵤ`, proton to atomic mass ratio `μₚᵤ`, proton to electron mass ratio `μₚₑ`, inverted fine structure constant `αinv`, and the gravitaional coupling constant `αG`.

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
