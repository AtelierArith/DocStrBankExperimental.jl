```
level_spacing(spect::UnfoldedSpectrum; n::Int = 1) → s::Vector
```

Return the level spacings of order `n`.  The nearest neighbour level spacings are the default, given by n=1.

## Description

The level spacings of order n are given by the difference between the n-th consecutive levels of the spectrum.  The nearest neighbour level spacing is considered most commonly. 

## Arguments

  * `spect`: The unfolded energy spectrum, given as an instance of type [`UnfoldedSpectrum`](@ref).

## Keyword arguments

  * `n=1` : The order of the level spacings.

## Returns

  * `s` : Vector of level spacings.
