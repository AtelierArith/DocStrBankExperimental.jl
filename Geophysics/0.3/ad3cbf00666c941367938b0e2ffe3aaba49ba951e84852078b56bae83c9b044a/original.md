```
thermalconductivity(F::FluidState) = conductivity(temperature(F),fluid(F))
```

Laminar thermal conductivity `k` at the temperature `F` (W⋅m⁻¹⋅K⁻¹ or lb⋅s⁻¹⋅°R⁻¹).
