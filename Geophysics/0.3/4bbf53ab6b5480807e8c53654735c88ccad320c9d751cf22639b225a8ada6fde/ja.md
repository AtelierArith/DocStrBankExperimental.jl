```
specificenergy(h::Real=0,W::Weather) = specificenergy(temperature(h,W),fluid(W))
```

特定エネルギー `e` は、`Weather` の位置の高度 `h` での値です (J⋅kg⁻¹ または ft⋅lb⋅slug⁻¹)。
