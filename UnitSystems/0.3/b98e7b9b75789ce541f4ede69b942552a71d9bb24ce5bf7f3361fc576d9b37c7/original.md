```Julia
earthcoulomb(U::UnitSystem) = charge(𝟏,U,Meridian)
```

Meridian unit of `charge` (C).

```Julia
julia> earthcoulomb(Metric) # C
1.0028982054691058

julia> earthcoulomb(EMU) # abC
0.10028982054691056

julia> earthcoulomb(ESU) # statC
3.0066131814137225e9
```
