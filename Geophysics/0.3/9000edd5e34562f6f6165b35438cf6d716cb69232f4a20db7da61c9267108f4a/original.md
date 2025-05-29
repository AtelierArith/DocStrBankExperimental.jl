```
thermaldiffusivity(F::FluidState) = thermalconductivity(F)/heatcapacity(F)
```

Thermal diffusivity `α` at a pressure and temperature (m²⋅s⁻¹ or ft²⋅s⁻¹).
