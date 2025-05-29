```
specificimpedance(F::FluidState) = density(F)*sonicspeed(F)
```

圧力と温度における特定の音響抵抗 (kg⋅m⁻³⋅s⁻¹ または slug⋅ft⁻³⋅s⁻¹)。
