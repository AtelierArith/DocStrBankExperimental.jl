```
entropy_wavelet(x; wavelet = Wavelets.WT.Daubechies{12}(), base = 2)
```

Compute the wavelet entropy. This function is just a convenience call to:

```julia
est = WaveletOverlap(wavelet)
information(Shannon(base), est, x)
```

See [`WaveletOverlap`](@ref) for more info.
