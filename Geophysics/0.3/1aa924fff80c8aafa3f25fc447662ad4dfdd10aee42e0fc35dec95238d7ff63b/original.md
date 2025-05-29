```
thermalconductivity(h::Real=0,W::Weather) = thermalconductivity(temperature(h,W),fluid(W))
```

Laminar thermal conductivity `k` at altitude `h` of `Weather` (W⋅m⁻¹⋅K⁻¹ or lb⋅s⁻¹⋅°R⁻¹).
