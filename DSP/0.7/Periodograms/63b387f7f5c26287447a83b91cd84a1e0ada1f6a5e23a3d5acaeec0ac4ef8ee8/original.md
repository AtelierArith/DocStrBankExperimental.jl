```
mt_cross_power_spectra(signal::AbstractMatrix{T}; fs=1, kwargs...) where {T}
mt_cross_power_spectra(signal::AbstractMatrix, config::MTCrossSpectraConfig)
```

Computes multitapered cross power spectra between channels of a signal. Arguments:

  * `signal`: `n_channels` x `n_samples`
  * Optionally pass an [`MTCrossSpectraConfig`](@ref) object to preallocate temporary variables

and choose configuration settings. Otherwise, any keyword arguments accepted by [`MTCrossSpectraConfig`](@ref) may be passed here.

Produces a `CrossPowerSpectra` object holding the `n_channels` x `n_channels` x `n_frequencies` output array (accessed by [`power`](@ref)) and the corresponding frequencies (accessed by [`freq`](@ref)).

See also [`mt_cross_power_spectra!`](@ref) and [`MTCrossSpectraConfig`](@ref).
