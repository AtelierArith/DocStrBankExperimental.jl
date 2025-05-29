```Julia
gasgallon(U::UnitSystem) = 𝟐*𝟑*𝟏𝟗*kilo*thermalunit(U)
```

Gasoline gallon equivalent reference unit of `energy` (J or lb⋅ft).

```Julia
julia> gasgallon(Metric) # J
1.2027456665017478e8

julia> gasgallon(CGS) # erg
1.2027456665017475e15

julia> gasgallon(British) # lb⋅ft
8.87099678818946e7
```
