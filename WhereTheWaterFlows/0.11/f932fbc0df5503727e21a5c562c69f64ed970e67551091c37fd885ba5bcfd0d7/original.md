```
catchment_flux(cellarea, c, color) = sum(cellarea[c.==color])
catchment_flux(cellarea, c::Union{BitArray, Matrix{Bool}})
```

The total flux, i.e. input, in one catchment.
