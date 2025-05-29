```
sonicspeed(h::Real=0,W::Weather) = sonicspeed(temperature(h,W),fluid(W))
```

Speed of sound wave disturbance at altitude `h` of `Weather` location (m⋅s⁻¹ or ft⋅s⁻¹).
