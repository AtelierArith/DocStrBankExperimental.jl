```
MTConfig{T}(n_samples; fs=1,
        nfft = nextpow(2, n_samples),
        window = nothing,
        nw = 4,
        ntapers = 2 * nw - 1,
        taper_weights = fill(1/ntapers, ntapers),
        onesided::Bool=T<:Real,
        fft_flags = FFTW.MEASURE)
```

Creates a config object which holds the configuration state and temporary variables used in multitaper computations, e.g. [`mt_pgram!`](@ref), [`mt_spectrogram`](@ref), [`MTSpectrogramConfig`](@ref), [`MTCrossSpectraConfig`](@ref), and [`MTCoherenceConfig`](@ref).

An `MTConfig` can be re-used between computations as long as none of the input arguments change.

  * `n_samples`: the number of samples to be used as input when computing multitaper periodograms with this configuration. Used for pre-allocating temporary buffers.
  * `fs`: the number of samples per second of the input signal
  * `nfft`: length of input vector to the FFT; if `nfft > n_samples`, then the input signal will be zero-padded until it is of length `nfft`.
  * `window`: window function to use for tapering. If left at the default of `nothing`, `window` will be set to `dpss(n_samples, nw, ntapers)`.
  * `ntapers`: the number of tapers to use.
  * `taper_weights = fill(1/ntapers, ntapers)`: how to weight the contribution of each taper. The default setting is to simply average them.
  * `onesided`: whether or not to compute a "one-sided" FFT by using that real signal data yields conjugate-symmetry in Fourier space.
  * `fft_flags`: flags to control how the FFT plan is generated.
