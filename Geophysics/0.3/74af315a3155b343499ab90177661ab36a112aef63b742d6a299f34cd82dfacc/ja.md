```
heatcapacity(h::Real=0,W::Weather=Standard) = heatcapacity(W(h))
```

特定の高度 `h` における `Weather` の位置での質量あたりの比熱 (J⋅m⁻³⋅K⁻¹ または lb⋅ft⁻²⋅°R⁻¹)。
