```
thermaldiffusivity(h::Real=0,W::Weather=Standard) = thermaldiffusivity(W(h))
```

Thermal diffusivity `α` at altitude `h` of `Weather` location (m²⋅s⁻¹ or ft²⋅s⁻¹).
