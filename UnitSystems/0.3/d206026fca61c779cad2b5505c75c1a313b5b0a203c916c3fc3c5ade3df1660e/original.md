```Julia
frequency(U::UnitSystem,S::UnitSystem) = 1/time(U,S)
frequency(v::Real,U::UnitSystem,S::UnitSystem) = v/frequency(U,S)
```

Number of occurences per unit of time (Hz or s⁻¹), unit conversion factor.

```Julia
julia> frequency(IAU,Metric) day⋅s⁻¹
1.1574074074074073e-5
```
