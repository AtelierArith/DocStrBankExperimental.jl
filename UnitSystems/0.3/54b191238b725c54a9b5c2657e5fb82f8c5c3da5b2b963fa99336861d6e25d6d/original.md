```Julia
angstrom(U::UnitSystem) = hecto*pico*meter(U)
```

Metric unit of `length` (m or ft).

```Julia
julia> angstrom(CGS) # cm
9.999999999999999e-9

julia> angstrom(English) # ft
3.280839895013123e-10

julia> angstrom(IPS) # in
3.937007874015747e-9
```
