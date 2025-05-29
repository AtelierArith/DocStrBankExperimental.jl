```
elasticity(h::Real=0,W::Weather=Standard) = elasticity(W(h))
```

Bulk modulus of elasticity `B` at altitude `h` of `Weather` location (Pa or slug⋅ft⁻¹⋅s⁻²).
