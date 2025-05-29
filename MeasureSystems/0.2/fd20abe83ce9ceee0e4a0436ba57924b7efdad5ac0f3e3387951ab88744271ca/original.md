```Julia
degree(U::UnitSystem) = angle(𝟏,U,MetricDegree)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A⋅(τ⋅2⁻³3⁻²5⁻¹ = 0.017453292519943295) [ϕ] Unified
```

Unit of `angle` which divides a `turn` into `360` parts (rad).

```Julia
julia> degree(Engineering) # rad
τ⋅2⁻³3⁻²5⁻¹ = 0.017453292519943295 [rad] Engineering

julia> degree(MetricDegree) # deg
𝟏 = 1.0 [deg] MetricDegree

julia> degree(MetricArcminute) # amin
2²3⋅5 = 60.0 [amin] MetricArcminute

julia> degree(MetricArcsecond) # asec
2⁴3²5² = 3600.0 [asec] MetricArcsecond

julia> degree(MetricGradian) # gon
2⋅3⁻²5 = 1.1111111111111112 [gon] MetricGradian
```
