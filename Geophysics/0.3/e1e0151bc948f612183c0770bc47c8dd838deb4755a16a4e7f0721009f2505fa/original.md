```
specificweight(h::Real=0,W::Weather=Standard) = density(h,W)*gravity(h,W)
```

Specific weight at altitude `h` of `Weather` location (kg⋅m⁻²⋅s⁻² or slugs⋅ft⁻²⋅s⁻²).
