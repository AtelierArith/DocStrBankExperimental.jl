```
clamp01(x) -> y
```

Produce a value `y` that lies between 0 and 1, and equal to `x` when `x` is already in this range. Equivalent to `clamp(x, 0, 1)` for numeric values. For colors, this function is applied to each color channel separately.

See also: [`clamp01!`](@ref), [`clamp01nan`](@ref).
