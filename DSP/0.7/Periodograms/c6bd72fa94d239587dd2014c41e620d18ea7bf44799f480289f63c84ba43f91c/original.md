```
MTCoherenceConfig{T}(n_channels, n_samples; fs=1, demean=false, freq_range=nothing, kwargs...) where T
MTCoherenceConfig(cs_config::MTCrossSpectraConfig{T}) where {T}
MTCoherenceConfig(n_channels, mt_config::MTConfig{T}; demean=false, freq_range=nothing,
    ensure_aligned = T == Float32 || T == Complex{Float32}) where {T}
```

Creates a configuration object for coherences from a [`MTCrossSpectraConfig`](@ref). Provides a helper method with the same arugments as `MTCrossSpectraConfig` to construct the `MTCrossSpectraConfig` object.

See also [`mt_coherence`](@ref) and [`mt_coherence!`](@ref).
