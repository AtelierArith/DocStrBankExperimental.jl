```
level_spacing_pdf(model::Model, pts::Vector; n::Int = 1) → p::Vector
```

Return the analytical expression for the level spacing probability density function, corresponding to the chosen model, evaluated at positions `pts`.

## Description

The nearest neighbour level spacing distributions are the most commonly studied spectral statistics.

## Arguments

  * `model`: The model, given as an instance of a concrete subtype of [`Model`](@ref).
  * `pts`: The positions where probabability density function should be evaluated.

## Keyword arguments

  * `n=1` : The order of the level spacings.

## Returns

  * `p` : Vector of the probabilites.
