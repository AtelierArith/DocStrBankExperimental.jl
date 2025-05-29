```
specificvolume(h::Real=0,W::Weather=Standard) = specificvolume(W(h))
```

Specific volume per mass `v` at altitude `h` of `Weather` location (m³⋅kg⁻¹, ft³⋅slug⁻¹).
