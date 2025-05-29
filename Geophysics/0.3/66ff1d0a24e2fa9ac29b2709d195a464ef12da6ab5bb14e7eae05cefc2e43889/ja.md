```
specificenthalpy(h::Real=0,W::Weather) = specificenthalpy(temperature(h,W),fluid(W))
```

特定エンタルピー `h` は `Weather` の位置の高度での値 (J⋅kg⁻¹ または ft⋅lb⋅slug⁻¹)。
