```
mt_coherence(signal::AbstractMatrix{T}; fs=1, freq_range = nothing, demean=false, kwargs...) where T
mt_coherence(signal::AbstractMatrix, config::MTCoherenceConfig)
```

Arguments:

  * `signal`: `n_channels` x `n_samples` matrix
  * Optionally pass an `MTCoherenceConfig` to pre-allocate temporary variables and choose configuration settings, otherwise, see [`MTCrossSpectraConfig`](@ref) for the meaning of the keyword arguments.

Returns a `Coherence` object.

See also [`mt_coherence`](@ref) and [`MTCoherenceConfig`](@ref).
