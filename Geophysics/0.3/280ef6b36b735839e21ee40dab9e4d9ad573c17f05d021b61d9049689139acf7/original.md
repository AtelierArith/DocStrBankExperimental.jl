```
heatpressure(F::FluidState) = heatpressure(temperature(F),fluid(F))
```

Specific heat `cₚ` at the temperature of `F` (J⋅kg⁻¹⋅K⁻¹ or ft⋅lb⋅slug⁻¹⋅°R⁻¹).
