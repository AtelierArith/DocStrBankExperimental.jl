```
bubble_temperature(model::EoSModel, p, x,method::BubblePointMethod = ChemPotBubbleTemperature())
```

Calculates the bubble temperature and properties at a given pressure. Returns a tuple, containing:

  * Bubble Temperature `[K]`
  * liquid volume at Bubble Point [`m³`]
  * vapour volume at Bubble Point [`m³`]
  * Gas composition at Bubble Point

By default, uses equality of chemical potentials, via [`ChemPotBubbleTemperature`](@ref)
