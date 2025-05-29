```Julia
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
angle(U::UnitSystem,S::UnitSystem) = angle(U,S)
angle(v::Real,U::UnitSystem,S::UnitSystem) = v/angle(U,S)
A [ϕ] Unified
```

Extent of one-dimensional angle or `angle` (rad), unit conversion factor.

```Julia
julia> angle(CGS,Metric) # rad⋅rad⁻¹
𝟏 = 1.0 [𝟙]/[𝟙] Metric -> Gauss
```
