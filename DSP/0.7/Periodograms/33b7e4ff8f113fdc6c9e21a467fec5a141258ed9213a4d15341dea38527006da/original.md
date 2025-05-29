```
mt_cross_power_spectra!(output, signal::AbstractMatrix; fs=1, kwargs...)
mt_cross_power_spectra!(output, signal::AbstractMatrix, config::MTCrossSpectraConfig)
```

Computes multitapered cross power spectra between channels of a signal. Arguments:

  * `output`: `n_channels` x `n_channels` x `length(config.freq)`. Can be created by `DSP.allocate_output(config)`.
  * `signal`: `n_channels` x `n_samples`
  * `config`: `MTCrossSpectraConfig{T}`: optionally pass a [`MTCrossSpectraConfig`](@ref) to preallocate temporary and choose configuration settings. Otherwise, one may pass any keyword arguments accepted by this object.

Produces a `CrossPowerSpectra` object holding the `n_channels` x `n_channels` x `n_frequencies` output array and the corresponding frequencies (accessed by [`freq`](@ref)).

See also [`mt_cross_power_spectra`](@ref) and [`MTCrossSpectraConfig`](@ref).
