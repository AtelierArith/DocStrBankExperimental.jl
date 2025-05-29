```
gravity(h::Real=0,W::Weather=Standard) = gravity(W)*radius(W)^2/altabs(h,W)^2
```

Gravitational acceleration `g` at altitude `h` of `Weather` column (m⋅s⁻² or ft⋅s⁻²).
