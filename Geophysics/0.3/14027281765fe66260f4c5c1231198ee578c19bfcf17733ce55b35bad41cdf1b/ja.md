```
specificenthalpy(F::FluidState) = specificenthalpy(temperature(F),fluid(F))
```

流体状態 `F` の温度における比エンタルピー `h` (J⋅kg⁻¹ または ft⋅lb⋅slug⁻¹)。
