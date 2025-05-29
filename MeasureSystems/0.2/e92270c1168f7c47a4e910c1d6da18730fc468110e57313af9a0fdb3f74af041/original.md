```Julia
turn(U::UnitSystem) = 2π/angle(U)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A⋅(τ = 6.283185307179586) [ϕ] Unified
```

Complete rotation `angle` of revolution from a full circle.

```Julia
julia> turn(Engineering) # rad
τ = 6.283185307179586 [rad] Engineering

julia> turn(MetricDegree) # deg
2³3²5 = 360.0 [deg] MetricDegree

julia> turn(MetricArcminute) # amin
2⁵3³5² = 21600.0 [amin] MetricArcminute

julia> turn(MetricArcsecond) # asec
2⁷3⁴5³ = 1.296×10⁶ [asec] MetricArcsecond

julia> turn(MetricGradian) # gon
2⁴5² = 400.0 [gon] MetricGradian
```
