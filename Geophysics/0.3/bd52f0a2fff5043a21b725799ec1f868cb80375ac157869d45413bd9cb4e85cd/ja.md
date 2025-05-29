```
heatvolume(h::Real=0,W::Weather) = heatvolume(temperature(h,W),fluid(W))
```

特定熱 `cᵥ` は、`Weather` 列の高度 `h` における値 (J⋅kg⁻¹⋅K⁻¹ または ft⋅lb⋅slug⁻¹⋅°R⁻¹) です。
