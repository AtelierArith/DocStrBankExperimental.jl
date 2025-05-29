```Julia
radiationdensity(U::UnitSystem) = 𝟐^2*stefan(U)/lightspeed(U)
```

黒体放射の放射密度定数 (J⋅m⁻³⋅K⁻⁴ または lb⋅ft⁻²⋅°R⁻⁴)。

```Julia
julia> radiationdensity(Metric) # J⋅m⁻³⋅K⁻⁴
7.565733239877308e-16

julia> radiationdensity(SI2019) # J⋅m⁻³⋅K⁻⁴
7.565733250280007e-16

julia> radiationdensity(Conventional) # J⋅m⁻³⋅K⁻⁴
7.565731760500178e-16

julia> radiationdensity(CODATA) # J⋅m⁻³⋅K⁻⁴
7.565722855744968e-16

julia> radiationdensity(International) # J⋅m⁻³⋅K⁻⁴
7.564484894028585e-16
```
