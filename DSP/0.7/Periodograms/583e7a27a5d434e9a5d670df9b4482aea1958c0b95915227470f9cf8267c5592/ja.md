```
mt_coherence(signal::AbstractMatrix{T}; fs=1, freq_range = nothing, demean=false, kwargs...) where T
mt_coherence(signal::AbstractMatrix, config::MTCoherenceConfig)
```

引数:

  * `signal`: `n_channels` x `n_samples` 行列
  * 必要に応じて `MTCoherenceConfig` を渡して一時変数を事前に割り当て、設定を選択します。そうでない場合は、キーワード引数の意味については [`MTCrossSpectraConfig`](@ref) を参照してください。

`Coherence` オブジェクトを返します。

他に [`mt_coherence`](@ref) および [`MTCoherenceConfig`](@ref) も参照してください。
