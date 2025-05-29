```Julia
gravity(U::UnitSystem) = # mass*acceleration/force
gravityforce : [F⁻¹MLT⁻²], [𝟙], [𝟙], [𝟙], [𝟙]
F⁻¹MLT⁻² [g₀] Unified
```

Gravitational force reference used in technical engineering units (kg⋅m⋅N⁻¹⋅s⁻²).

```Julia
julia> gravity(Metric)
𝟏 = 1.0 [𝟙] Metric

julia> gravity(Engineering) # m⋅kg⋅N⁻¹⋅s⁻²
g₀ = 9.80665 [kgf⁻¹kg⋅m⋅s⁻²] Engineering

julia> gravity(English) # ft⋅lbm⋅lbf⁻¹⋅s⁻²
g₀⋅ft⁻¹ = 32.17404855643044 [lbf⁻¹lbm⋅ft⋅s⁻²] English
```
