```
scalesigned(maxabs) -> f
```

Return a function `f` which scales values in the range `[-maxabs, maxabs]` (clamping values that lie outside this range) to the range `[-1, 1]`.

See also: [`colorsigned`](@ref).
