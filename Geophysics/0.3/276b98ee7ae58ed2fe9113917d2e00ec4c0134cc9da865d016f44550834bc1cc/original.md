```
heatvolume(F::FluidState) = heatvolume(temperature(F),fluid(F))
```

Specific heat `cᵥ` at the temperature of `F` (J⋅kg⁻¹⋅K⁻¹ or ft⋅lb⋅slug⁻¹⋅°R⁻¹).
