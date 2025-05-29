```
heatvolume(F::FluidState) = heatvolume(temperature(F),fluid(F))
```

特定熱 `cᵥ` は `F` の温度での値 (J⋅kg⁻¹⋅K⁻¹ または ft⋅lb⋅slug⁻¹⋅°R⁻¹)。
