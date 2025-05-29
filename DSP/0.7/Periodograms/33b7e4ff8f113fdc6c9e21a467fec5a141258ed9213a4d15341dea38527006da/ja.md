```
mt_cross_power_spectra!(output, signal::AbstractMatrix; fs=1, kwargs...)
mt_cross_power_spectra!(output, signal::AbstractMatrix, config::MTCrossSpectraConfig)
```

信号のチャネル間のマルチテーパー交差パワースペクトルを計算します。引数：

  * `output`: `n_channels` x `n_channels` x `length(config.freq)`。`DSP.allocate_output(config)`によって作成できます。
  * `signal`: `n_channels` x `n_samples`
  * `config`: `MTCrossSpectraConfig{T}`: 一時的なメモリを事前に割り当て、設定を選択するために[`MTCrossSpectraConfig`](@ref)をオプションで渡します。そうでない場合、このオブジェクトが受け入れる任意のキーワード引数を渡すことができます。

`n_channels` x `n_channels` x `n_frequencies`の出力配列と対応する周波数（[`freq`](@ref)でアクセス）を保持する`CrossPowerSpectra`オブジェクトを生成します。

また、[`mt_cross_power_spectra`](@ref)および[`MTCrossSpectraConfig`](@ref)も参照してください。
