```Julia
spatian(U::UnitSystem) = angle(𝟏,U,MetricSpatian)
angle : [A], [𝟙], [𝟙], [𝟙], [𝟙]
A⋅(τ¹ᐟ²2¹ᐟ² = 3.5449077018110318) [ϕ] Unified
```

Unit of `angle` which is dimensionless (rad).

```Julia
julia> spatian(Engineering) # rad
τ¹ᐟ²2¹ᐟ² = 3.5449077018110318 [rad] Engineering

julia> spatian(MetricDegree) # deg
τ⁻¹ᐟ²2⁷ᐟ²3²5 = 203.1082500771923 [deg] MetricDegree

julia> spatian(MetricArcminute) # amin
τ⁻¹ᐟ²2¹¹ᐟ²3³5² = 12186.495004631537 [amin] MetricArcminute

julia> spatian(MetricArcsecond) # asec
τ⁻¹ᐟ²2¹⁵ᐟ²3⁴5³ = 731189.7002778922 [asec] MetricArcsecond

julia> spatian(MetricGradian) # gon
τ⁻¹ᐟ²2⁹ᐟ²5² = 225.67583341910253 [gon] MetricGradian
```
