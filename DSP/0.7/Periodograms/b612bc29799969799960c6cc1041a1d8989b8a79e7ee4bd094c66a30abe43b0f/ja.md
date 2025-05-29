```
mt_spectrogram(signal::AbstractVector{T}, n::Int=length(s) >> 3,
                              n_overlap::Int=n >> 1; fs=1,
                              onesided::Bool=T <: Real, kwargs...) where {T}
mt_spectrogram(signal::AbstractVector, config::MTSpectrogramConfig)
```

マルチテーパーのスペクトログラムを計算し、`Spectrogram`オブジェクトを返します。オプションで[`MTSpectrogramConfig`](@ref)オブジェクトを渡すことができます。そうでない場合は、[`MTConfig`](@ref)によって受け入れられる追加のキーワード引数を渡してテーパーの設定を行うことができます。

`Spectrogram`を返します。

さらに[`mt_spectrogram!`](@ref)も参照してください。
