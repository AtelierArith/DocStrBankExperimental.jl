```
cylinder(cx, cy, cz, wx, wy, wz, Φ, Θ, value::Number)
cylinder(center::NTuple{3,RealU}, width::NTuple{3,RealU}, angle::NTuple{3,RealU}, v)
```

Construct `Object{Cylinder}` from parameters; here `width` is the *radius* in x,y and the *height* in z.
