```Julia
rem(U::UnitSystem) = centi*gray(U)
```

放射能の古い単位 (Gy または m²⋅s⁻²)。

```Julia
julia> rem(Metric) # Sv
0.01
```
