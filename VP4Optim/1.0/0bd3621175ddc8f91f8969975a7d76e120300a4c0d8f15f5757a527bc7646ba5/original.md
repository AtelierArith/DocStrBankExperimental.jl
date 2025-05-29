```
c(mod::Model)
```

Return VARPRO vector `c`.

## Default

  * Gets `B` and `b` from [Bb!](@ref Bb!) and calculates generic solution `c = B \ b`.

## Remarks

  * Can be replaced by model-specific implementation, if desired (e.g. for performance improvements).
