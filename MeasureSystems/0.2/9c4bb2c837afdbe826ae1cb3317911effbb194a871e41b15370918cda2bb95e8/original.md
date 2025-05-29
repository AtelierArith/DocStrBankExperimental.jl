```Julia
angularfrequency : [T⁻¹A], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
angularfrequency(U::UnitSystem,S::UnitSystem) = angle(U,S)/time(U,S)
angularfrequency(v::Real,U::UnitSystem,S::UnitSystem) = v/angularfrequency(U,S)
T⁻¹A [ħ⁻¹𝘤²mₑ⋅g₀⁻¹] Unified
```

Circular radian frequency (rad⋅Hz or rad⋅s⁻¹), unit conversion factor.

```Julia
julia> angularfrequency(IAU,Metric) day⋅s⁻¹
2⁻⁷3⁻³5⁻² = 1.1574074074074075×10⁻⁵ [Hz]/[D⁻¹] IAU☉ -> Metric
```
