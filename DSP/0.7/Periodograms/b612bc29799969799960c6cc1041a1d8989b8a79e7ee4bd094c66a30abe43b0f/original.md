```
mt_spectrogram(signal::AbstractVector{T}, n::Int=length(s) >> 3,
                              n_overlap::Int=n >> 1; fs=1,
                              onesided::Bool=T <: Real, kwargs...) where {T}
mt_spectrogram(signal::AbstractVector, config::MTSpectrogramConfig)
```

Compute a multitaper spectrogram, returning a `Spectrogram` object. Optionally pass a [`MTSpectrogramConfig`](@ref) object; otherwise, any additional keyword arguments accepted by [`MTConfig`](@ref) may be passed to configure the tapering.

Returns a `Spectrogram`.

See also [`mt_spectrogram!`](@ref).
