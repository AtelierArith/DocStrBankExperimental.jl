```Julia
magneticfluxdensity(U::UnitSystem,S::UnitSystem) = magneticflux(U,S)/area(U,S)
magneticfluxdensity(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticfluxdensity(U,S)
```

Magnetic induction or `magneticmoment` per `volume` (T or Wb⋅m⁻²), unit conversion factor.

```Julia
julia> magneticfluxdensity(EMU,Metric) # T⋅G⁻¹
9.999999999999995e-5

julia> magneticfluxdensity(EMU,ESU) # statT⋅G⁻¹
3.33564095198152e-11

julia> magneticfluxdensity(Metric,SI2019) # T⋅T⁻¹
1.0000000002726048
```
