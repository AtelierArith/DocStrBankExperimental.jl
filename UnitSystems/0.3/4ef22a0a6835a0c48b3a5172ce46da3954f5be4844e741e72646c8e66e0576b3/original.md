```Julia
numberdensity(U::UnitSystem,S::UnitSystem) = 1/volume(U,S)
numberdensity(v::Real,U::UnitSystem,S::UnitSystem) = v/numberdensity(U,S)
```

Number per `volume` or `numberdensity` (m⁻³ or ft⁻³), unit conversion factor.

```Julia
julia> numberdensity(CGS,Metric) # cm³⋅m⁻³
999999.9999999995

julia> numberdensity(English,Metric) # ft³⋅m⁻³
35.31466672148858
```
