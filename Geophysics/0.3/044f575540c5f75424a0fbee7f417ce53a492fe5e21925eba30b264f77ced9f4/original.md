```
kinematic(h::Real=0,W::Weather=Standard) = kinematic(W(h))
```

Kinematic viscosity ratio `ν` at altitude `h` of `Weather` location (m²⋅s⁻¹ or ft²⋅s⁻¹).
