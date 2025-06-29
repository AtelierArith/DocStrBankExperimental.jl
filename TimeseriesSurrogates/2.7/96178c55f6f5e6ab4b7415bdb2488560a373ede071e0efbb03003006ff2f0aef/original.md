```
TFTS(fϵ::Real)
```

A truncated Fourier transform surrogate[^Nakamura2006] (TFTS).

TFTS surrogates are generated by leaving some frequencies untouched when performing the phase shuffling step (as opposed to randomizing all frequencies, like for [`RandomFourier`](@ref) surrogates).

These surrogates were designed to deal with data with irregular fluctuations superimposed over long term trends (by preserving low frequencies)[^Nakamura2006]. Hence, TFTS surrogates can be used to test the null hypothesis that the signal is a stationary linear system generated the irregular fluctuations part of the signal[^Nakamura2006].

## Controlling the truncation of the spectrum

The truncation parameter `fϵ ∈ [-1, 0) ∪ (0, 1]` controls which parts of the spectrum are preserved.

  * If `fϵ > 0`, then `fϵ` indicates the ratio of high frequency domain to the entire frequency domain.   For example, `fϵ = 0.5` preserves 50% of the frequency domain (randomizing the higher   frequencies, leaving low frequencies intact).
  * If `fϵ < 0`, then `fϵ` indicates ratio of low frequency domain to the entire frequency domain.   For example, `fϵ = -0.2` preserves 20% of the frequency domain (leaving higher frequencies intact,   randomizing the lower frequencies).
  * If `fϵ ± 1`, then all frequencies are randomized. The method is then equivalent to   [`RandomFourier`](@ref).

The appropriate value of `fϵ` strongly depends on the data and time series length, and must be manually determined[^Nakamura2006], for example by comparing periodograms for the time series and the surrogates.

[^Nakamura2006]: Nakamura, Tomomichi, Michael Small, and Yoshito Hirata. "Testing for nonlinearity in irregular fluctuations with long-term trends." Physical Review E 74.2 (2006): 026205.
