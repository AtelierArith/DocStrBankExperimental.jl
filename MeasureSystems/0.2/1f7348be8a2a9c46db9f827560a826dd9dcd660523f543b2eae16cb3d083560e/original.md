```Julia
spat(U::UnitSystem) = 4π/solidangle(U)
solidangle : [A²], [𝟙], [𝟙], [𝟙], [𝟙]
A²⋅(τ⋅2 = 12.566370614359172) [ϕ²] Unified
```

Complete spherical `solidangle` around point from a full sphere.

```Julia
julia> spat(Engineering) # rad²
τ⋅2 = 12.566370614359172 [rad²] Engineering

julia> spat(MetricDegree) # deg²
τ⁻¹2⁷3⁴5² = 41252.96124941928 [deg²] MetricDegree

julia> spat(MetricArcminute) # amin²
τ⁻¹2¹¹3⁶5⁴ = 1.485106604979094×10⁸ [amin²] MetricArcminute

julia> spat(MetricArcsecond) # asec²
τ⁻¹2¹⁵3⁸5⁶ = 5.346383777924738×10¹¹ [asec²] MetricArcsecond

julia> spat(MetricGradian) # gon²
τ⁻¹2⁹5⁴ = 50929.58178940651 [gon²] MetricGradian
```
