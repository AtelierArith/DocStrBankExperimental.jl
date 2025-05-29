```Julia
wienwavelength(U::UnitSystem) = planck(U)*lightspeed(U)/boltzmann(U)/(𝟓+W₀(-𝟓*exp(-𝟓)))
nonstandard : [LΘ], [LΘ], [LΘ], [LΘ], [LΘ]
LΘ/4.965114231744276 [kB⁻¹ħ⋅𝘤⋅ϕ] Unified
```

Wien wavelength displacement law constant based on Lambert `W₀` evaluation (m⋅K or ft⋅°R).

```Julia
julia> wienwavelength(Metric) # m⋅K
kB⁻¹NA⁻¹𝘤²R∞⁻¹α²μₑᵤ⋅2⁻⁴5⁻³/4.965114231744276 = 0.00289777195618(89) [m⋅K] Metric

julia> wienwavelength(SI2019) # m⋅K
kB⁻¹𝘩⋅𝘤/4.965114231744276 = 0.0028977719551851727 [m⋅K] SI2019

julia> wienwavelength(Conventional) # m⋅K
kB⁻¹NA⁻¹𝘤²R∞⁻¹α²μₑᵤ⋅2⁻⁴5⁻³/4.965114231744276 = 0.00289777195618(89) [m⋅K] Conventional

julia> wienwavelength(CODATA) # m⋅K
𝘤²R∞⁻¹α²μₑᵤ⋅Rᵤ2014⁻¹2⁻⁴5⁻³/4.965114231744276 = 0.0028977729(17) [m⋅K] CODATA

julia> wienwavelength(English) # ft⋅°R
kB⁻¹NA⁻¹𝘤²R∞⁻¹α²μₑᵤ⋅ft⁻¹2⁻⁴3²5⁻⁴/4.965114231744276 = 0.0171128265129(53) [ft⋅°R] English
```
