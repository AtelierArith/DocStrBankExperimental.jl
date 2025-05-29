```
mt_cross_power_spectra(signal::AbstractMatrix{T}; fs=1, kwargs...) where {T}
mt_cross_power_spectra(signal::AbstractMatrix, config::MTCrossSpectraConfig)
```

信号のチャネル間のマルチテーパー交差パワースペクトルを計算します。引数:

  * `signal`: `n_channels` x `n_samples`
  * 一時変数を事前に割り当てるために、オプションで[`MTCrossSpectraConfig`](@ref)オブジェクトを渡すことができます。

設定を選択します。そうでない場合は、ここで[`MTCrossSpectraConfig`](@ref)が受け入れる任意のキーワード引数を渡すことができます。

`n_channels` x `n_channels` x `n_frequencies`の出力配列を保持する`CrossPowerSpectra`オブジェクトを生成します（[`power`](@ref)でアクセス）および対応する周波数（[`freq`](@ref)でアクセス）。

[`mt_cross_power_spectra!`](@ref)および[`MTCrossSpectraConfig`](@ref)も参照してください。
