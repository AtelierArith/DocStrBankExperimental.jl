```Julia
luminousefficacy : [F⁻¹L⁻¹TJ], [F⁻¹L⁻¹TJ], [M⁻¹L⁻²T³J], [M⁻¹L⁻²T³J], [M⁻¹L⁻²T³J]
luminousefficacy(U::UnitSystem,S::UnitSystem) = luminousefficacy(S)/luminousefficacy(U)
luminousefficacy(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousefficacy(U,S)
F⁻¹L⁻¹TJ [Kcd] Unified
```

Ratio of `luminousflux` to `power` or `luminousefficacy` (lm⋅W⁻¹), unit conversion factor.

```Julia
julia> luminousefficacy(CGS,Metric) # erg⋅s⁻¹⋅W⁻¹
2⁷5⁷ = 1.0×10⁷ [J⁻¹]/[erg⁻¹] Gauss -> Metric

julia> luminousefficacy(English,Metric) # ft⋅lb⋅s⁻¹⋅W⁻¹
g₀⁻¹ft⁻¹lb⁻¹ = 0.7375621492772653 [J⁻¹]/[lbf⁻¹ft⁻¹] English -> Metric
```
