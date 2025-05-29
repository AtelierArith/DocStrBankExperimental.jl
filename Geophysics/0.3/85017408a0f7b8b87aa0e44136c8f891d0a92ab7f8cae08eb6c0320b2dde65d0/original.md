```
viscosity(h::Real=0,W::Weather) = viscosity(temperature(h,W),fluid(W))
```

Laminar dynamic vicsosity `μ` at altitude `h` of `Weather` column (Pa⋅s or slug⋅ft⁻¹⋅s⁻¹).
