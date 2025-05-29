```
scale(r::ParamRange)
```

Return the scale associated with a `ParamRange` object `r`. The possible return values are: `:none` (for a `NominalRange`), `:linear`, `:log`, `:log10`, `:log2`, or `:custom` (if `r.scale` is a callable object).
