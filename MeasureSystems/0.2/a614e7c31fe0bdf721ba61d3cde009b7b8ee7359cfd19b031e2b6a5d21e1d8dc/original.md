```Julia
molality : [M⁻¹N], [F⁻¹LT⁻²N], [M⁻¹N], [M⁻¹N], [M⁻¹N]
molality(U::UnitSystem,S::UnitSystem) = molarmass(U)/molarmass(S)
molality(v::Real,U::UnitSystem,S::UnitSystem) = v/molality(U,S)
M⁻¹N [Mᵤ⁻¹] Unified
```

Molality or `mole` per `mass` (mol⋅kg⁻¹), unit conversion factor.

```Julia
julia> molality(CGS,Metric) # kg⋅g⁻¹
2³5³ = 1000.0 [kg⁻¹]/[g⁻¹] Gauss -> Metric

julia> molality(Metric,SI2019) # mol⋅mol⁻¹
NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅2⁻⁴5⁻³ = 1.00000000034(31) [mol]/[mol] Metric -> SI2019
```
