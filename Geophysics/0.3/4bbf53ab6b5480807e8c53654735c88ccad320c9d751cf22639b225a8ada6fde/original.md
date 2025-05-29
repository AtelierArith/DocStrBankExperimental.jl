```
specificenergy(h::Real=0,W::Weather) = specificenergy(temperature(h,W),fluid(W))
```

Specific energy `e` at altitude `h` of `Weather` location (J⋅kg⁻¹ or ft⋅lb⋅slug⁻¹).
