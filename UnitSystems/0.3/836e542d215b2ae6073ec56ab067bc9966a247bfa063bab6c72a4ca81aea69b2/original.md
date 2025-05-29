```Julia
solidangle(U::UnitSystem,S::UnitSystem) = angle(U,S)^2
solidangle(v::Real,U::UnitSystem,S::UnitSystem) = v/solidangle(U,S)
```

Extent of two-dimensional angle or `solidangle` (rad²), unit conversion factor.

```Julia
julia> solidangle(CGS,Metric) # rad²⋅rad⁻²
1
```
