```
PrecomputedLowfreqPowerSpectrum
```

A struct containing all the precomputed fields to efficiently perform repetitive computation of the low-frequency power spectrum (LFPS), a number between `0` and `1` that characterizes the amount of power contained in the low frequencies of the power density spectrum of `x`. Once `lfps::PrecomputedLowfreqPowerSpectrum` is initialized, it can be used as a function to obtain the LFPS of `x::AbstractVector` by:

```julia
lfps(x)
```
