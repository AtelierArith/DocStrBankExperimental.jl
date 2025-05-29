```
periodogram(s; onesided=eltype(s)<:Real, nfft=nextfastfft(n), fs=1, window=nothing)
```

Computes periodogram of a signal by FFT and returns a Periodogram object.

For real signals, the two-sided periodogram is symmetric and this function returns a one-sided (real only) periodogram by default. A two-sided periodogram can be obtained by setting `onesided=false`.

`nfft` specifies the number of points to use for the Fourier transform. If `length(s)` < `nfft`, then the input is padded with zeros. By default, `nfft` is the closest size for which the Fourier transform can be computed with maximal efficiency.

`fs` is the sample rate of the original signal, and `window` is an optional window function or vector to be applied to the original signal before computing the Fourier transform. The computed periodogram is normalized so that the area under the periodogram is equal to the uncentered variance (or average power) of the original signal.
