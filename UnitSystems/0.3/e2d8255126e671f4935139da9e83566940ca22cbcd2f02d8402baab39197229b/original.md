```Julia
angularwavenumber(U::UnitSystem,S::UnitSystem) = angle(U,S)/length(U,S)
angularwavenumber(v::Real,U::UnitSystem,S::UnitSystem) = v/angularwavenumber(U,S)
```

Number of occurences per unit of space (m⁻¹), unit conversion factor.

```Julia
julia> angularwavenumber(CGS,Metric) # cm⋅m⁻¹
99.99999999999999

julia> angularwavenumber(English,Metric) # ft⋅m⁻¹
3.280839895013123
```
