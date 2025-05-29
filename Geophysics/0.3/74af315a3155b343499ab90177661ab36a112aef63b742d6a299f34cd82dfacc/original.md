```
heatcapacity(h::Real=0,W::Weather=Standard) = heatcapacity(W(h))
```

Specific heat per mass at altitude `h` of `Weather` location (J⋅m⁻³⋅K⁻¹ or lb⋅ft⁻²⋅°R⁻¹).
