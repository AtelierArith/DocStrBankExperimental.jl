```
specificimpedance(h::Real=0,W::Weather=Standard) = impedance(W(h))
```

Specific acoustic resistance at altitude `h` of `Weather` (kg⋅m⁻³⋅s⁻¹ or slug⋅ft⁻³⋅s⁻¹).
