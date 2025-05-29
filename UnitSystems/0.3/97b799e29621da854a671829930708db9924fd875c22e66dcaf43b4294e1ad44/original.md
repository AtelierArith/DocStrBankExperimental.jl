```Julia
angularfrequency(U::UnitSystem,S::UnitSystem) = angle(U,S)/time(U,S)
angularfrequency(v::Real,U::UnitSystem,S::UnitSystem) = v/angularfrequency(U,S)
```

Circular radian frequency (rad⋅Hz or rad⋅s⁻¹), unit conversion factor.

```Julia
julia> angularfrequency(IAU,Metric) day⋅s⁻¹
1.1574074074074073e-5
```
