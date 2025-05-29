```
elasticity(F::FluidState) = heatratio(F)*pressure(F)
```

圧力と温度における体積弾性率 `B` (Pa または slug⋅ft⁻¹⋅s⁻²)。
