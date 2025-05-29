```
mt_coherence!(output, signal::AbstractMatrix; fs=1, freq_range=nothing, demean=false, kwargs...)
mt_coherence!(output, signal::AbstractMatrix, config::MTCoherenceConfig)
```

Computes the pairwise coherences between channels.

  * `output`: `n_channels` x `n_channels` matrix
  * `signal`: `n_samples` x `n_channels` matrix
  * `config`: optional configuration object that pre-allocates temporary variables and choose settings.

Returns a `Coherence` object.

See also [`mt_coherence`](@ref) and [`MTCoherenceConfig`](@ref).
