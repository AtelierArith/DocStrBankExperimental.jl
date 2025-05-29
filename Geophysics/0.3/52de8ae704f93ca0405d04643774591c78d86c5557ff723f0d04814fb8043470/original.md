```
heatpressure(h::Real=0,W::Weather) = heatpressure(temperature(h,W),fluid(W))
```

Specific heat `cₚ` at atltitude `h` of `Weather` column (J⋅kg⁻¹⋅K⁻¹ or ft⋅lb⋅slug⁻¹⋅°R⁻¹).
