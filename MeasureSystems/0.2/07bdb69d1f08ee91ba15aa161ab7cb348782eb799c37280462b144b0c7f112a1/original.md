```Julia
bubnoff(U::UnitSystem) = meter(U)/year(U)
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
LT⁻¹⋅(𝘤⁻¹aⱼ⁻¹2⁻⁷3⁻³5⁻² = 1.0570008340246154×10⁻¹⁶) [𝘤] Unified
```

Reference unit of erosion `speed` (m⋅s⁻¹ or ft⋅s⁻¹).

```Julia
julia> bubnoff(CGS) # cm⋅s⁻¹
aⱼ⁻¹2⁻⁵3⁻³ = 3.1688087814028946×10⁻⁶ [cm⋅s⁻¹] Gauss

julia> bubnoff(English) # ft⋅s⁻¹
aⱼ⁻¹ft⁻¹2⁻⁷3⁻³5⁻² = 1.0396354269694536×10⁻⁷ [ft⋅s⁻¹] English
```
