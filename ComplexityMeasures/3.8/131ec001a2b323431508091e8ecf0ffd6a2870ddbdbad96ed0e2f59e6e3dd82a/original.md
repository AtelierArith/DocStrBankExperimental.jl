```
WaveletOverlap([wavelet]) <: OutcomeSpace
```

An [`OutcomeSpace`](@ref) based on the maximal overlap discrete wavelet transform (MODWT).

When used with [`probabilities`](@ref), the MODWT is applied to a signal, then probabilities are computed as the (normalized) energies at different wavelet scales. These probabilities are used to compute the wavelet entropy according to [Rosso2001](@citet). Input timeseries `x` is needed for a well-defined outcome space.

By default the wavelet `Wavelets.WT.Daubechies{12}()` is used. Otherwise, you may choose a wavelet from the `Wavelets` package (it must subtype `OrthoWaveletClass`).

## Outcome space

The outcome space for `WaveletOverlap` are the integers `1, 2, …, N` enumerating the wavelet scales. To obtain a better understanding of what these mean, we prepared a notebook you can [view online](https://github.com/kahaaga/waveletentropy_example/blob/main/wavelet_entropy_example.ipynb). As such, this estimator only works for timeseries input and input `x` is needed for a well-defined [`outcome_space`](@ref).
