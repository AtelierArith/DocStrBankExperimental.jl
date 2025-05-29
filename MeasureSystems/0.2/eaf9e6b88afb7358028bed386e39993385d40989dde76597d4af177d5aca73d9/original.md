```
mechanicalheat(U::UnitSystem) = molargas(U)/molargas(Metric)*calorie(Metric)
energy : [FL], [FL], [ML²T⁻²], [ML²T⁻²], [ML²T⁻²]
```

Heat to raise 1 `mass` unit of water by 1 `temperature` unit, or kB⋅NA⋅Ωᵢₜ⋅Vᵢₜ⁻²2⁻²3⁻²5⁻¹43 = 1.9859050081929637 `mechanicalheat` per `molaramount` per `temperature` units (J or ft⋅lb).

```Julia
julia> mechanicalheat(Metric) # J
Ωᵢₜ⁻¹Vᵢₜ²2²3²5⋅43⁻¹ = 4.186737323211057 [J] Metric

julia> mechanicalheat(English) # ft⋅lb
g₀⁻¹ft⁻¹Ωᵢₜ⁻¹Vᵢₜ²2⁵5⁵43⁻¹ = 778.1576129990752 [lbf⋅ft] English

julia> mechanicalheat(British) # ft⋅lb
ft⁻²Ωᵢₜ⁻¹Vᵢₜ²2⁵5⁵43⁻¹ = 25036.480825188257 [lb⋅ft] British
```
