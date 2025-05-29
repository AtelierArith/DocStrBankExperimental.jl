```
level_spacing_u(model::Model, pts::Vector; n::Int = 1) → u::Vector
```

Return the analytical expression for the spectraly normalized cumulative density function of the nearest neighbour level spacings evaluated at positions `pts`.

## Arguments

  * `model`: The model, given as an instance of a concrete subtype of [`Model`](@ref).
  * `pts`: The positions where cumulative density function should be evaluated.

## Keyword arguments

  * `n=1` : The order of the level spacings.

## Returns

  * `u` : Vector of the cumulative probabilities.
