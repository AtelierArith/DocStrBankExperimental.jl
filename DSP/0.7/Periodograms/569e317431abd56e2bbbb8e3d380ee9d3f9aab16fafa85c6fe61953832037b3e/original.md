```
spectrogram(s, n=div(length(s), 8), noverlap=div(n, 2); onesided=eltype(s)<:Real, nfft=nextfastfft(n), fs=1, window=nothing)
```

Computes the spectrogram of a signal `s` based on segments with `n` samples with overlap of `noverlap` samples, and returns a Spectrogram object. See [`periodogram`](@ref) for description of optional keyword arguments.
