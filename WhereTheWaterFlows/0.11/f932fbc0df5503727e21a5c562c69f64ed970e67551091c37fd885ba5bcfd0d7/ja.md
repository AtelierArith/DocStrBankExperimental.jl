```
catchment_flux(cellarea, c, color) = sum(cellarea[c.==color])
catchment_flux(cellarea, c::Union{BitArray, Matrix{Bool}})
```

1つの流域における総フラックス、すなわち入力。
