```Julia
demagnetizingfactor(U::UnitSystem,S::UnitSystem) = 1/susceptibility(U,S)
demagnetizingfactor(v::Real,U::UnitSystem,S::UnitSystem) = v/demagnetizingfactor(U,S)
```

Quantitiy of `demagnetizingfactor` (dimensionless), unit conversion factor.

```Julia
julia> demagnetizingfactor(EMU,Metric)
0.07957747154594767

julia> demagnetizingfactor(ESU,Metric)
0.07957747154594767

julia> demagnetizingfactor(Metric,SI2019)
1
```
