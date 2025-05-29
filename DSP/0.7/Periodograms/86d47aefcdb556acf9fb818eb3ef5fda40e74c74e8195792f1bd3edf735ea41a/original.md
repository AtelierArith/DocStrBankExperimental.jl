```
MTCrossSpectraConfig{T}(n_channels, n_samples; fs=1, demean=false, freq_range=nothing,
                        ensure_aligned = T == Float32 || T == Complex{Float32}, kwargs...) where {T}
MTCrossSpectraConfig(n_channels, mt_config::MTConfig{T}; demean=false, freq_range=nothing,
                     ensure_aligned = T == Float32 || T == Complex{Float32})
```

Creates a configuration object used for [`mt_cross_power_spectra`](@ref) and [`mt_cross_power_spectra!`](@ref).

  * `n_channels`: the number of channels of the input.
  * `n_samples`: the number of samples for each channel of the input.
  * `demean`: if `true`, the channelwise mean will be subtracted from the input signals before the cross spectral powers are computed.
  * `freq_range`: if `nothing`, all frequencies are retained. Otherwise, only frequencies between `first(freq_range)` and `last(freq_range)` are retained.
  * `ensure_aligned = T == Float32 || T == Complex{Float32}`: perform an extra copy to ensure that the FFT output is memory-aligned
  * Additionally, either pass an [`MTConfig`](@ref) object, or keyword arguments such as `fs` accepted by [`MTConfig`](@ref).

Returns a `CrossPowerSpectra` object.
