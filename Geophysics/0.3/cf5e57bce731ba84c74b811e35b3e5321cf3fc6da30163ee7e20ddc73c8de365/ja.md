```
specificenergy(F::FluidState) = specificenergy(temperature(F),fluid(F))
```

流体状態 `F` の温度における比エネルギー `e` (J⋅kg⁻¹ または ft⋅lb⋅slug⁻¹)。
