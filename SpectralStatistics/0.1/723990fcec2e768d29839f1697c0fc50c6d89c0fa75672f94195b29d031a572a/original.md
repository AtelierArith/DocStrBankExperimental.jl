```
level_spacing_cdf(spect::UnfoldedSpectrum, pts::Vector; n::Int = 1) → s::Vector w::Vector
```

Return the cumulative density function of the level spacings of order `n` evaluated at positions `pts`. The nearest neighbour level spacings are the default, given by n=1.

## Arguments

  * `spect`: The unfolded energy spectrum, given as an instance of type [`UnfoldedSpectrum`](@ref).
  * `pts`: The positions where cumulative density function should be evaluated.

## Keyword arguments

  * `n=1` : The order of the level spacings.

## Returns

  * `w` : Vector of the cumulative probabilities.
