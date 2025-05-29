```
cone(cx, cy, cz, wx, wy, wz, Φ, Θ, value::Number)
cone(center::NTuple{3,RealU}, width::NTuple{3,RealU}, angle::NTuple{3,RealU}, v)
```

Construct `Object{Cone}` from parameters; here `width` is the base radii for `wx` and `wy` and `wz` is the height.
