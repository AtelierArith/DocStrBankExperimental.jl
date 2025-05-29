```
heatvolume(h::Real=0,W::Weather) = heatvolume(temperature(h,W),fluid(W))
```

Specific heat `cᵥ` at altitude `h` of `Weather` column (J⋅kg⁻¹⋅K⁻¹ or ft⋅lb⋅slug⁻¹⋅°R⁻¹).
