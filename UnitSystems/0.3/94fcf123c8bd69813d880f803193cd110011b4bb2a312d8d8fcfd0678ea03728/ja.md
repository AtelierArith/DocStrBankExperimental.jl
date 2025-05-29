```Julia
lightspeed(U::UnitSystem) = 𝟏/sqrt(vacuumpermeability(U)*vacuumpermittivity(U))/lorentz(U)
```

真空中の光速 `𝘤` は、質量のない粒子のための (m⋅s⁻¹ または ft⋅s⁻¹)。

```Julia
julia> lightspeed(Metric) # m⋅s⁻¹
2.99792458e8

julia> lightspeed(English) # ft⋅s⁻¹
9.835710564304461e8

julia> lightspeed(IAU) # au⋅D⁻¹
173.14463267424034
```
