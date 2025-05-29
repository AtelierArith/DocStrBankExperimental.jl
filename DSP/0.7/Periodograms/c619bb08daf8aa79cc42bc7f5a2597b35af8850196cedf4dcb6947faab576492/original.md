```
mt_spectrogram!(output, signal::AbstractVector{T}, n::Int=length(signal) >> 3,
    n_overlap::Int=n >> 1; fs=1, onesided::Bool=T <: Real, kwargs...) where {T}
mt_spectrogram!(destination::AbstractMatrix, signal::AbstractVector, config::MTSpectrogramConfig)
```

Computes a multitaper spectrogram using the parameters specified in `config`. Arguments:

  * `destination`: `length(config.mt_config.freq)` x `length(config.time)` matrix. This can be created by `DSP.allocate_output(config)`.
  * `signal`: vector of length `config.n_samples`
  * `config`: optionally, pass an [`MTSpectrogramConfig`](@ref) object to hold temporary variables and configuration settings. Otherwise, settings arguments may be passed directly.

Returns a `Spectrogram`.

See also [`mt_spectrogram`](@ref).
