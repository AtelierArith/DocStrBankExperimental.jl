```Julia
specificvolume(U::UnitSystem,S::UnitSystem) = volume(U,S)/mass(U,S)
specificvolume(v::Real,U::UnitSystem,S::UnitSystem) = v/specificvolume(U,S)
```

Reciprocal `density` or `volume` per `mass` or `specificvolume` (m³⋅kg), unit conversion factor.

```Julia
julia> specificvolume(CGS,Metric) # g⋅m³⋅kg⁻¹⋅cm⁻³
0.0010000000000000007

julia> specificvolume(CGS,British) # kg⋅ft³⋅slug⁻¹⋅cm⁻³
0.5153788183931961

julia> specificvolume(English,Metric) # lb⋅m³⋅kg⁻¹⋅ft⁻³
0.062427960576144616
```
