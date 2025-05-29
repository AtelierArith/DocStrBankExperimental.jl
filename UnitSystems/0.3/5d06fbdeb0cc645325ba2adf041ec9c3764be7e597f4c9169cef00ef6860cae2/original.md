```
μₑᵤ, μₚᵤ, μₚₑ, αinv, αG, ΩΛ
```

Physical measured dimensionless `Coupling` values with uncertainty are the electron to proton mass ratio `μₑᵤ`, proton to atomic mass ratio `μₚᵤ`, proton to electron mass ratio `μₚₑ`, inverted fine structure constant `αinv`, and the gravitaional coupling constant `αG`.

```Julia
julia> μₑᵤ # electronunit(Universe)
0.0005485799090649074

julia> μₚᵤ # protonunit(Universe)
1.007276466621

julia> μₚₑ # protonelectron(Universe)
1836.152673432705

julia> αinv # 1/finestructure(Universe)
137.035999084

julia> αG # coupling(Universe)
1.751809945750515e-45

julia> ΩΛ # darkenergydensity(Universe)
0.6889
```
