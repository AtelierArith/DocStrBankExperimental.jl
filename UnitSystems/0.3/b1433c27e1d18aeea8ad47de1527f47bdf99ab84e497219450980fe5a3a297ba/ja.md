```Julia
electronmass(U::UnitSystem) = protonmass(U)/protonelectron(U) # αinv^2*R∞*2𝘩/𝘤
```

電子の静止質量 `mₑ` は、`-𝘦` の素電荷を持つ亜原子粒子の質量 (kg またはスラグ)。

```Julia
julia> electronmass(Metric) # kg
9.109383701558256e-31

julia> electronmass(CODATA) # kg
9.10938354907983e-31

julia> electronmass(Conventional) # kg
9.109381920341098e-31

julia> electronmass(International) # kg
9.107880653411075e-31

julia> electronmass(Metric)/dalton(Metric) # Da
0.0005485799090649074

julia> electronmass(QCD) # mₚ
0.0005446170214868301

julia> electronmass(Hartree) # mₑ
1

julia> electronmass(Metric)*lightspeed(Metric)^2 # J
8.187105776876243e-14

julia> electronmass(SI2019)*lightspeed(SI2019)^2/elementarycharge(SI2019) # eV⋅𝘤⁻²
510998.9499994321

julia> electronmass(English) # lb
2.0082753379555867e-30
```
