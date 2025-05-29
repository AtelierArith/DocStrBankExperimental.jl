```
bubble_pressure(model::EoSModel, T, x, method = ChemPotBubblePressure())
```

Calculates the bubble pressure and properties at a given temperature. Returns a tuple, containing:

  * Bubble Pressure `[Pa]`
  * liquid volume at Bubble Point [`m³`]
  * vapour volume at Bubble Point [`m³`]
  * Gas composition at Bubble Point

By default, uses equality of chemical potentials, via [`ChemPotBubblePressure`](@ref)
