```
kinematic(h::Real=0,W::Weather=Standard) = kinematic(W(h))
```

高度 `h` の `Weather` ロケーションにおける運動粘度比 `ν` (m²⋅s⁻¹ または ft²⋅s⁻¹)。
