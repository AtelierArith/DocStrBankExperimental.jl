```Julia
gravity(U::UnitSystem) = # mass*acceleration/force
```

Gravitational force reference used in technical engineering units (kg⋅m⋅N⁻¹⋅s⁻²).

```Julia
julia> gravity(Metric)
1

julia> gravity(Engineering) # m⋅kg⋅N⁻¹⋅s⁻²
9.80665

julia> gravity(English) # ft⋅lbm⋅lbf⁻¹⋅s⁻²
32.17404855643044
```
