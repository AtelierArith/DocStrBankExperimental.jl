```
PowerSpectrum() <: OutcomeSpace
```

An [`OutcomeSpace`](@ref) based on the power spectrum of a timeseries (amplitude square of its Fourier transform).

If used with [`probabilities`](@ref), then the spectrum normalized to sum = 1 is returned as probabilities. The Shannon entropy of these probabilities is typically referred in the literature as *spectral entropy*, e.g. [Llanos2017](@citet) and [Tian2017](@citet).

The closer the spectrum is to flat, i.e., white noise, the higher the entropy. However, you can't compare entropies of timeseries with different length, because the binning in spectral space depends on the length of the input.

## Outcome space

The outcome space `Ω` for `PowerSpectrum` is the set of frequencies in Fourier space. They should be multiplied with the sampling rate of the signal, which is assumed to be `1`. Input `x` is needed for a well-defined [`outcome_space`](@ref).
