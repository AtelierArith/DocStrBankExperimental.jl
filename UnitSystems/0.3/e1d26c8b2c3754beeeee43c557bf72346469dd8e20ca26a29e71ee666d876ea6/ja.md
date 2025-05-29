```Julia
wienwavelength(U::UnitSystem) = planck(U)*lightspeed(U)/boltzmann(U)/(𝟓+W₀(-𝟓*exp(-𝟓)))
```

ウィーン波長変位法則定数は、ランベルト `W₀` の評価に基づいています (m⋅K または ft⋅°R)。

```Julia
julia> wienwavelength(Metric) # m⋅K
0.002897771956181264

julia> wienwavelength(SI2019) # m⋅K
0.0028977719551851727

julia> wienwavelength(Conventional) # m⋅K
0.0028977719561812647

julia> wienwavelength(CODATA) # m⋅K
0.002897772938369599

julia> wienwavelength(English) # ft⋅°R
0.017112826512881478
```
