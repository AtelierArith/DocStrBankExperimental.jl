```
pressure(h::Real=0,W::Weather=Standard) = pressure(W(h))
```

Absolute force per unit area `P`  at altitude `h` of `Weather` column (Pa or slug⋅ft⁻¹⋅s⁻²).
