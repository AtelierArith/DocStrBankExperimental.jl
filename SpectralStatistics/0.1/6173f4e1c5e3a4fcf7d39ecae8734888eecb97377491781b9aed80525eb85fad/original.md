```
level_spacing_cdf(model::Model, pts::Vector; n::Int = 1) → w::Vector
```

Return the analytical expression for level spacing cumulative density function, corresponding to the chosen model, evaluated at positions `pts`.

## Arguments

  * `model`: The model, given as an instance of a concrete subtype of [`Model`](@ref).
  * `pts`: The positions where cumulative density function should be evaluated.

## Keyword arguments

  * `n=1` : The order of the level spacings.

## Returns

  * `w` : Vector of the cumulative probabilities.
