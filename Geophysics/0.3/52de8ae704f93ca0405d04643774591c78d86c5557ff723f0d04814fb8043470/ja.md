```
heatpressure(h::Real=0,W::Weather) = heatpressure(temperature(h,W),fluid(W))
```

特定熱 `cₚ` は、`Weather` 列の高度 `h` におけるものであり (J⋅kg⁻¹⋅K⁻¹ または ft⋅lb⋅slug⁻¹⋅°R⁻¹)。
