```Julia
solidangle : [A²], [𝟙], [𝟙], [𝟙], [𝟙]
solidangle(U::UnitSystem,S::UnitSystem) = angle(U,S)^2
solidangle(v::Real,U::UnitSystem,S::UnitSystem) = v/solidangle(U,S)
A² [ϕ²] Unified
```

Extent of two-dimensional angle or `solidangle` (rad²), unit conversion factor.

```Julia
julia> solidangle(CGS,Metric) # rad²⋅rad⁻²
𝟏 = 1.0 [𝟙]/[𝟙] Gauss -> Metric
```
