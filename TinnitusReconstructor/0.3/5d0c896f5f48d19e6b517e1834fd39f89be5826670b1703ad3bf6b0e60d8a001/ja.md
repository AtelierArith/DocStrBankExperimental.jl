```
GaussianPrior(; kwargs...) <: BinnedStimgen
```

刺激生成タイプで、充填されたビンの数が既知の平均と分散パラメータを持つガウス分布から選択されます。

# キーワード

  * `min_freq::Real = 100`: サンプリングする範囲の最小周波数。
  * `max_freq::Real = 22e3`: サンプリングする範囲の最大周波数。
  * `duration::Real = 0.5`: 刺激が再生される時間の長さ（秒）。
  * `Fs::Real = 44.1e3`: 刺激の周波数（Hz）。
  * `n_bins_filled_var::Real = 1`: 任意の刺激で充填される可能性のあるビンの数の分散。
  * `n_bins_filled_mean::Integer = 20`: 任意の刺激で充填される可能性のあるビンの数の平均。
  * `n_bins::Integer = 100`: 周波数範囲を分割するビンの数。
