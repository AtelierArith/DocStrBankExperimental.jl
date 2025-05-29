```Julia
angle(U::UnitSystem,S::UnitSystem) = angle(U,S)
angle(v::Real,U::UnitSystem,S::UnitSystem) = v/angle(U,S)
```

Extent of one-dimensional angle or `angle` (rad), unit conversion factor.

```Julia
julia> angle(CGS,Metric) # rad⋅rad⁻¹
1
```
