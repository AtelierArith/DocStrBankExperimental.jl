```Julia
radian(U::UnitSystem) = angle(𝟏,U,Metric)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A [ϕ] Unified
```

Unit of `angle` which is dimensionless (rad).

```Julia
julia> radian(Engineering) # rad
𝟏 = 1.0 [rad] Engineering

julia> radian(MetricDegree) # deg
τ⁻¹2³3²5 = 57.29577951308232 [deg] MetricDegree

julia> radian(MetricArcminute) # amin
τ⁻¹2⁵3³5² = 3437.7467707849396 [amin] MetricArcminute

julia> radian(MetricArcsecond) # asec
τ⁻¹2⁷3⁴5³ = 206264.80624709636 [asec] MetricArcsecond

julia> radian(MetricGradian) # gon
τ⁻¹2⁴5² = 63.66197723675814 [gon] MetricGradian
```
