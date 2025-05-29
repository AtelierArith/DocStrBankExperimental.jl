```Julia
photonintensity : [T⁻¹A⁻²], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
photonintensity(U::UnitSystem,S::UnitSystem) = frequency(U,S)/solidangle(U,S)
photonintensity(v::Real,U::UnitSystem,S::UnitSystem) = v/photonintensity(U,S)
T⁻¹A⁻² [ħ⁻¹𝘤²mₑ⋅ϕ⁻³g₀⁻¹] Unified
```

Photon intensity or `frequency` per `area` (Hz⋅m⁻², m⁻²⋅s⁻¹), unit conversion factor.

```Julia
julia> photonintensity(IAU,Metric) day⋅s⁻¹
2⁻⁷3⁻³5⁻² = 1.1574074074074075×10⁻⁵ [Hz]/[D⁻¹] IAU☉ -> Metric
```
