```
prandtl(h::Real=0,W::Weather) = prandtl(temperature(h,W),fluid(W))
```

Prandtl number at altitude `h` of `Weather` location (dimensionless).
