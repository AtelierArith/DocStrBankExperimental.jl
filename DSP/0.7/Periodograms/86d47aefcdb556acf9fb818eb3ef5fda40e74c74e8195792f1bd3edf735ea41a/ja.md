```
MTCrossSpectraConfig{T}(n_channels, n_samples; fs=1, demean=false, freq_range=nothing,
                        ensure_aligned = T == Float32 || T == Complex{Float32}, kwargs...) where {T}
MTCrossSpectraConfig(n_channels, mt_config::MTConfig{T}; demean=false, freq_range=nothing,
                     ensure_aligned = T == Float32 || T == Complex{Float32})
```

[`mt_cross_power_spectra`](@ref) および [`mt_cross_power_spectra!`](@ref) に使用される構成オブジェクトを作成します。

  * `n_channels`: 入力のチャネル数。
  * `n_samples`: 入力の各チャネルのサンプル数。
  * `demean`: `true` の場合、クロススペクトルパワーが計算される前に、チャネルごとの平均が入力信号から引かれます。
  * `freq_range`: `nothing` の場合、すべての周波数が保持されます。それ以外の場合、`first(freq_range)` と `last(freq_range)` の間の周波数のみが保持されます。
  * `ensure_aligned = T == Float32 || T == Complex{Float32}`: FFT出力がメモリに整列されるように、追加のコピーを実行します。
  * さらに、[`MTConfig`](@ref) オブジェクトを渡すか、[`MTConfig`](@ref) によって受け入れられる `fs` のようなキーワード引数を渡します。

`CrossPowerSpectra` オブジェクトを返します。
