```
MTSpectrogramConfig(n_samples, mt_config::MTConfig{T}, n_overlap_samples) where {T}
MTSpectrogramConfig{T}(n_samples, samples_per_window, n_overlap_samples; fs=1, kwargs...) where {T}
```

`MTSpectrogramConfig`を作成し、[`mt_spectrogram`](@ref)および[`mt_spectrogram!`](@ref)のための設定と一時変数を保持します。[`MTConfig`](@ref)によって受け入れられる任意のキーワード引数をここに渡すことができ、または`MTConfig`オブジェクト自体を渡すことができます。
