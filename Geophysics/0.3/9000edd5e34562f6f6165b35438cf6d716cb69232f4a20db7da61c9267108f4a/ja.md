```
thermaldiffusivity(F::FluidState) = thermalconductivity(F)/heatcapacity(F)
```

熱拡散率 `α` は、圧力と温度における値 (m²⋅s⁻¹ または ft²⋅s⁻¹)。
