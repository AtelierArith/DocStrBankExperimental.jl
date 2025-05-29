```
compute_LSF_matrix(synth_wls, obs_wls, R; kwargs...)
```

Construct a sparse matrix, which when multiplied with a flux vector defined over wavelenths `synth_wls`, applies a gaussian line spead function (LSF) and resamples to the wavelenths `obswls`.

# Arguments

  * `synth_wls`: the synthesis wavelengths in any form recognized by `synthesize`, e.g. a pair containing a lower and upper bound in Å, a vector of pairs, or a vector of Julia range objects.
  * `obs_wls`: the wavelengths of the observed spectrum
  * `R`: the resolving power, $R = \lambda/\Delta\lambda$

# Keyword Arguments

  * `window_size` (default: 4): how far out to extend the convolution kernel in units of the LSF width (σ, not HWHM)
  * `verbose` (default: `true`): whether or not to emit warnings and information to stdout/stderr.
  * `step_tolerance`: the maximum difference between adjacent wavelengths in `synth_wls` for them to be considered linearly spaced.  This is only used if `synth_wls` is a vector of wavelengths rather than a range or vector or ranges.

For the best match to data, your wavelength range should extend a couple $\Delta\lambda$ outside the region you are going to compare.

[`Korg.apply_LSF`](@ref) can apply an LSF to a single flux vector efficiently. This function is relatively slow, but one the LSF matrix is constructed, convolving spectra to observational resolution via matrix multiplication is fast.
