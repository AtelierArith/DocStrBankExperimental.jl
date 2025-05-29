```Julia
wavenumber(U::UnitSystem,S::UnitSystem) = 1/length(U,S)
wavenumber(v::Real,U::UnitSystem,S::UnitSystem) = v/wavenumber(U,S)
```

Number of occurences per unit of space (m⁻¹), unit conversion factor.

```Julia
julia> wavenumber(CGS,Metric) # cm⋅m⁻¹
99.99999999999999

julia> wavenumber(English,Metric) # ft⋅m⁻¹
3.280839895013123
```
