```Julia
fuelefficiency(U::UnitSystem,S::UnitSystem) = 1/area(U,S)
fuelefficiency(v::Real,U::UnitSystem,S::UnitSystem) = v/fuelefficiency(U,S)
```

体積あたりの距離または燃料効率 (m⋅m⁻³, m⁻²)、単位変換係数。

```Julia
julia> fuelefficiency(CGS,Metric) # cm²⋅m⁻²
9999.999999999996

julia> fuelefficiency(English,Metric) # ft²⋅m⁻²
10.76391041670972
```
