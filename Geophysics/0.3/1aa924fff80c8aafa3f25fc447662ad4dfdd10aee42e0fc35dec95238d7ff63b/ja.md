```
thermalconductivity(h::Real=0,W::Weather) = thermalconductivity(temperature(h,W),fluid(W))
```

高度 `h` の `Weather` における層流熱伝導率 `k` (W⋅m⁻¹⋅K⁻¹ または lb⋅s⁻¹⋅°R⁻¹)。
