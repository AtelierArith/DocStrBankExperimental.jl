```
specificimpedance(h::Real=0,W::Weather=Standard) = impedance(W(h))
```

気象条件 `Weather` の高度 `h` における特定の音響抵抗 (kg⋅m⁻³⋅s⁻¹ または slug⋅ft⁻³⋅s⁻¹)。
