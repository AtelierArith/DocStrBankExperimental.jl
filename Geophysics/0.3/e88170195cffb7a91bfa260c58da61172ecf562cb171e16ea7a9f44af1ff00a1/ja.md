```
gravity(h::Real=0,W::Weather=Standard) = gravity(W)*radius(W)^2/altabs(h,W)^2
```

高度 `h` の `Weather` 列における重力加速度 `g` (m⋅s⁻² または ft⋅s⁻²)。
