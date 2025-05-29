```
apply_LSF(flux, wls, R; window_size=4)
```

Applies a gaussian line spread function the the spectrum with flux vector `flux` and wavelengths `wls` in any format accepted by synthesize, e.g. as a pair `(λstart, λstop)`) with constant spectral resolution (, $R = \lambda/\Delta\lambda$, where $\Delta\lambda$ is the LSF FWHM.  The `window_size` argument specifies how far out to extend the convolution kernel in standard deviations.

For the best match to data, your wavelength range should extend a couple $\Delta\lambda$ outside the region you are going to compare.

If you are convolving many spectra defined on the same wavelenths to observational resolution, you will get much better performance using [`compute_LSF_matrix`](@ref).

# Keyword Arguments

  * `window_size` (default: 4): how far out to extend the convolution kernel in units of the LSF width (σ, not HWHM)
  * `renormalize_edge` (default: `true`): whether or not to renormalize the LSF at the edge of the wl range.  This doen't matter as long as `synth_wls` extends to large and small enough wavelengths.

!!! warning
      * This is a naive, slow implementation.  Do not use it when performance matters.
      * `apply_LSF` will have weird behavior if your wavelength grid is not locally linearly-spaced. It is intended to be run on a fine wavelength grid, then downsampled to the observational (or otherwise desired) grid.

