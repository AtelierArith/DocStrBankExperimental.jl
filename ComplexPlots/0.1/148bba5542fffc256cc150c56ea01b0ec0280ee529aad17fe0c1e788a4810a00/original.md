```
artist(base=exp(1), colormap=Makie.ColorSchemes.cyclic_mygbm_30_95_c78_n256)
```

`artist(b)` returns a function that maps a complex number `z` to a color. The hue is determined by the angle of `z`. The value (lightness) is determined by the fractional part of $\log_b |z|$. You can optionally specify any colormap, though a cyclic one is strongly recommended.
