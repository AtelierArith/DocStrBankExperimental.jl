```
level_spacing_u(spect::UnfoldedSpectrum, pts::Vector; n::Int = 1) → s::Vector u::Vector
```

Return the spectraly normalized cumulative density function of the nearest neighbour level spacings evaluated at positions `pts`.

## Description

The nearest neighbour level spacing distributions are the most commonly studied spectral statistics. To normalize the relative fluctuations it is useful to perform the following nonlinear transformation

$$
U(s) := \frac{2}{\pi}\arccos\sqrt{1-W(s)},
$$

where $W(s)$ is the cumulative level spacing distribution.

## Arguments

  * `spect`: The unfolded energy spectrum, given as an instance of type [`UnfoldedSpectrum`](@ref).
  * `pts`: The positions where cumulative density function should be evaluated.

## Keyword arguments

  * `n=1` : The order of the level spacings.

## Returns

  * `u` : Vector of the cumulative probabilities.
