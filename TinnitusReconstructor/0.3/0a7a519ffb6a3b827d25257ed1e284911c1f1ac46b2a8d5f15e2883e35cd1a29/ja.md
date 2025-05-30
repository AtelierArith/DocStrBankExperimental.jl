```
Bernoulli(; kwargs...) <: BinnedStimgen
```

各トノトピックビンが0 dBである確率 `bin_prob` を持ち、それ以外の場合は-100 dBである刺激生成タイプです。

# キーワード

  * `min_freq::Real = 100`: サンプリングする範囲の最小周波数。
  * `max_freq::Real = 22e3`: サンプリングする範囲の最大周波数。
  * `duration::Real = 0.5`: 刺激が再生される時間の長さ（秒）。
  * `Fs::Real = 44.1e3`: 刺激の周波数（Hz）。
  * `bin_prob::Real=0.3`: ビンが埋まる確率。
  * `n_bins::Integer = 100`: 周波数範囲を分割するビンの数。
