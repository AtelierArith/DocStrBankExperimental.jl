```
heatratio(h::Real=0,W::Weather) = heatratio(temperature(h,W),fluid(W))
```

Specific heat ratio `γ` at altitude `h` of `Weather` location (dimensionless).
