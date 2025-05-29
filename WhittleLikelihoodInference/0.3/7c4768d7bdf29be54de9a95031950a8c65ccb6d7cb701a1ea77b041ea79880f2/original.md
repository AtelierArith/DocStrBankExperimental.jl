```
BartlettPeriodogram(timeseries, Δ, segmentlength)
```

Compute the Bartlett periodogram for the provided timeseries with sampling rate Δ.

# Arguments

  * `timeseries`: A `Vector` if univariate and an `n` by `d` `Matrix` if multivariate, where `n` is the number of observations and `d` is the dimension of the timeseries.
  * `Δ`: A positive real number.
  * `segmentlength`: the length of series used in each segment.

Computes an estimate of the spectral density function using Bartlett's method. Using the same normalisation as `Periodogram`.

# External links

  * [Bartlett's method on Wikipedia](https://en.wikipedia.org/wiki/Bartlett%27s_method)
