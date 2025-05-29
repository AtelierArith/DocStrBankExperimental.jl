```
spectrum_correlation_fft(tlist, corr; inverse=false)
```

Calculate the power spectrum corresponding to a two-time correlation function using fast Fourier transform (FFT).

# Parameters

  * `tlist::AbstractVector`: List of times at which the two-time correlation function is given.
  * `corr::AbstractVector`: List of two-time correlations corresponding to the given time point in `tlist`.
  * `inverse::Bool`: Whether to use the inverse Fourier transform or not. Default to `false`.

# Returns

  * `ωlist`: the list of angular frequencies $\omega$.
  * `Slist`: the list of the power spectrum corresponding to the angular frequencies in `ωlist`.
