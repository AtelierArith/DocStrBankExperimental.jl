```
mt_spectrogram!(output, signal::AbstractVector{T}, n::Int=length(signal) >> 3,
    n_overlap::Int=n >> 1; fs=1, onesided::Bool=T <: Real, kwargs...) where {T}
mt_spectrogram!(destination::AbstractMatrix, signal::AbstractVector, config::MTSpectrogramConfig)
```

`config`で指定されたパラメータを使用してマルチテーパーのスペクトログラムを計算します。引数:

  * `destination`: `length(config.mt_config.freq)` x `length(config.time)` 行列。これは `DSP.allocate_output(config)` によって作成できます。
  * `signal`: 長さ `config.n_samples` のベクトル
  * `config`: 一時変数と設定を保持するために [`MTSpectrogramConfig`](@ref) オブジェクトをオプションで渡します。そうでない場合、設定引数を直接渡すことができます。

`Spectrogram` を返します。

さらに [`mt_spectrogram`](@ref) を参照してください。
