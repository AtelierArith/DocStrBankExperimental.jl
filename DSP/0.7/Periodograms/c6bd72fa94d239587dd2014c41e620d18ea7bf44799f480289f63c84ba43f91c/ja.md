```
MTCoherenceConfig{T}(n_channels, n_samples; fs=1, demean=false, freq_range=nothing, kwargs...) where T
MTCoherenceConfig(cs_config::MTCrossSpectraConfig{T}) where {T}
MTCoherenceConfig(n_channels, mt_config::MTConfig{T}; demean=false, freq_range=nothing,
    ensure_aligned = T == Float32 || T == Complex{Float32}) where {T}
```

[`MTCrossSpectraConfig`](@ref) からコヒーレンスのための設定オブジェクトを作成します。`MTCrossSpectraConfig` と同じ引数を持つヘルパーメソッドを提供し、`MTCrossSpectraConfig` オブジェクトを構築します。

[`mt_coherence`](@ref) および [`mt_coherence!`](@ref) も参照してください。
