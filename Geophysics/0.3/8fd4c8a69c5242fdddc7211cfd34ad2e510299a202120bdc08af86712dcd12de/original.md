```
intensity(h::Real=0,W::Weather=Standard) = intensity(W(h))
```

Instantaneous intensity `I` at altitude `h` of `Weather` at location (W⋅m⁻² or slug⋅s⁻³).
