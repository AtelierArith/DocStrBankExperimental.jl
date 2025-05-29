```
thermalconductivity(F::FluidState) = conductivity(temperature(F),fluid(F))
```

温度 `F` における層流熱伝導率 `k` (W⋅m⁻¹⋅K⁻¹ または lb⋅s⁻¹⋅°R⁻¹)。
