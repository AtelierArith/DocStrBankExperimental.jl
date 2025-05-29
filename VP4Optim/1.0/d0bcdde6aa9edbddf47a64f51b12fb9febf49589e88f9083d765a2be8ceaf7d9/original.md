```
χ2(mod::Model)
```

Return `χ² = y² - b' * (B \ b)` of actual model.

## Default

  * Uses `mod.y2` and `(B, b)` from [Bb!](@ref Bb!) to directly calculate the expression.
