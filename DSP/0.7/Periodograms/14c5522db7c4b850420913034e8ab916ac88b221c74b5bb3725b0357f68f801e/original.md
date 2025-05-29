```
MTSpectrogramConfig(n_samples, mt_config::MTConfig{T}, n_overlap_samples) where {T}
MTSpectrogramConfig{T}(n_samples, samples_per_window, n_overlap_samples; fs=1, kwargs...) where {T}
```

Creates a `MTSpectrogramConfig` which holds configuration and temporary variables for [`mt_spectrogram`](@ref) and [`mt_spectrogram!`](@ref). Any keyword arguments accepted by [`MTConfig`](@ref) may be passed here, or an `MTConfig` object itself.
