```Julia
arcminute(U::UnitSystem) = angle(𝟏,U,MetricArcminute)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A⋅(τ⋅2⁻⁵3⁻³5⁻² = 0.00029088820866572163) [ϕ] Unified
```

Unit of `angle` which divides a `degree` into `60` parts (rad).

```Julia
julia> arcminute(Engineering) # rad
τ⋅2⁻⁵3⁻³5⁻² = 0.00029088820866572163 [rad] Engineering

julia> arcminute(MetricDegree) # deg
2⁻²3⁻¹5⁻¹ = 0.016666666666666666 [deg] MetricDegree

julia> arcminute(MetricArcminute) # amin
𝟏 = 1.0 [amin] MetricArcminute

julia> arcminute(MetricArcsecond) # asec
2²3⋅5 = 60.0 [asec] MetricArcsecond

julia> arcminute(MetricGradian) # gon
2⁻¹3⁻³ = 0.018518518518518517 [gon] MetricGradian
```
