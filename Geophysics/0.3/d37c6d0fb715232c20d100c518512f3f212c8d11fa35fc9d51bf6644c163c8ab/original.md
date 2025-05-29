```
density(h::Real=0,W::Weather=Standard) = density(W(h))
```

Inertial mass per volume `ρ` at altitude `h` of `Weather` location (kg⋅m⁻³ or slugs⋅ft⁻³).
