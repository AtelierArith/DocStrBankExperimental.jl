```
viscosity(h::Real=0,W::Weather) = viscosity(temperature(h,W),fluid(W))
```

高度 `h` の `Weather` 列における層流動的粘度 `μ` (Pa⋅s または slug⋅ft⁻¹⋅s⁻¹)。
