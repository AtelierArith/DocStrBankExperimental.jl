```
normalize_hue(h::Real)
normalize_hue(c::Colorant)
```

Returns a normalized (wrapped-around) hue angle, or a color with the normalized hue, in degrees, in [0, 360]. The normalization is essentially equivalent to `mod(h, 360)`, but is faster at the expense of some accuracy.
