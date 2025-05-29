```
intensity_sppa(pressures::Array{Unitful.Pressure, N}, medium::Medium, excitation::Excitation)
```

Spatial Peak, Pulse Averaged intensity [W/cm²]

`pressures` is expected to be an array with up to 4 dimensions. The first dimension is time, and the remaining dimensions are space
