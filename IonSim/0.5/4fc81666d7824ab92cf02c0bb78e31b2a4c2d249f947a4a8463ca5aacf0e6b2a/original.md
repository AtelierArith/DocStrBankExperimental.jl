```
zeemanshift(I::Ion, sublevel, B::Real)
```

Returns the Zeeman shift at a magnetic field of `B` of `sublevel` of `I`. If `sublevel` has a custom g-factor defined, then this is used. Otherwise, `landegf` is used  to compute the Landé g-factor. Zeeman shift calculated as $ΔE = (μ_B/ħ) ⋅ g_f ⋅ B ⋅ m / 2π$
