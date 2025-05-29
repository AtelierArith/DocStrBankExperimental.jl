```Julia
meter(U::UnitSystem) = length(𝟏,U,Metric)
```

メートル法の`length` (m または ft)。

```Julia
julia> meter(CGS) # cm
99.99999999999999

julia> meter(English) # ft
3.280839895013123

julia> meter(Meridian) # em
0.9985540395253691
```
