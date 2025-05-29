```Julia
gaussianmonth(U::UnitSystem) = τ*sqrt(lunardistance(U)^3/earthmass(U)/gravitation(U))
time : [T], [T], [T], [T], [T]
T⋅1.6987431854323947e6 [ħ⋅𝘤⁻²mₑ⁻¹ϕ⋅g₀] Unified
```

Orbit `time` defined by `lunardistance` and `earthmass` for neglible `mass` satellite (s).

```Julia
julia> gaussianmonth(Metric) # s
GME⁻¹ᐟ²τ⋅2⁹ᐟ²3⁹ᐟ²5⁹ᐟ²⋅1.6987431854323947×10⁶ = 2.3718343493(24) × 10⁶ [s] Metric

julia> gaussianmonth(MPH) # h
GME⁻¹ᐟ²τ⋅2¹ᐟ²3⁵ᐟ²5⁵ᐟ²⋅1.6987431854323947×10⁶ = 658.84287479(66) [h] MPH

julia> gaussianmonth(IAU) # D
GME⁻¹ᐟ²τ⋅2⁻⁵ᐟ²3³ᐟ²5⁵ᐟ²⋅1.6987431854323947×10⁶ = 27.451786450(28) [D] IAU☉
```
