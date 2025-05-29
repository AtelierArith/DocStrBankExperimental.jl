```
mt_coherence!(output, signal::AbstractMatrix; fs=1, freq_range=nothing, demean=false, kwargs...)
mt_coherence!(output, signal::AbstractMatrix, config::MTCoherenceConfig)
```

チャネル間のペアワイズコヒーレンスを計算します。

  * `output`: `n_channels` x `n_channels` 行列
  * `signal`: `n_samples` x `n_channels` 行列
  * `config`: 一時変数を事前に割り当て、設定を選択するオプションの構成オブジェクト。

`Coherence` オブジェクトを返します。

[`mt_coherence`](@ref) および [`MTCoherenceConfig`](@ref) も参照してください。
