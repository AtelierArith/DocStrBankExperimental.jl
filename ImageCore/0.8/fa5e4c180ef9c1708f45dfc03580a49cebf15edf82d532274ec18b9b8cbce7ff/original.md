```
scalesigned(min, center, max) -> f
```

Return a function `f` which scales values in the range `[min, center]` to `[-1,0]` and `[center,max]` to `[0,1]`. Values smaller than `min`/`max` get clamped to `min`/`max`, respectively.

See also: [`colorsigned`](@ref).
