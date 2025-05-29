```
level_spacing_pdf(spect::UnfoldedSpectrum, bins::Vector; n::Int = 1) → s::Vector p::Vector
```

Return a histogram of the probability density function of the level spacings of order `n`. The nearest neighbour level spacings are the default, given by n=1.

## Description

The nearest neighbour level spacing distributions are the most commonly studied spectral statistics.

## Arguments

  * `spect`: The unfolded energy spectrum, given as an instance of type [`UnfoldedSpectrum`](@ref).
  * `bins`: The boundaries of the bin positions.

## Keyword arguments

  * `n=1` : The order of the level spacings.

## Returns

  * `p` : Vector of the probability contained in each bin.
