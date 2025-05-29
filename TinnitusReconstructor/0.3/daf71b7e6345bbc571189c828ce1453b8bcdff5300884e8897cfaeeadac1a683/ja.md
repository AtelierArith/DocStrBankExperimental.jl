```
UniformPriorWeightedSampling(; kwargs...) <: BinnedStimgen
```

各トノトピックビンが[`min_bins`, `max_bins`]の一様分布から埋められる刺激生成タイプですが、どのビンが埋められるかは非一様分布によって決まります。

# キーワード

  * `min_freq::Real = 100`: サンプリングする範囲の最小周波数。
  * `max_freq::Real = 22e3`: サンプリングする範囲の最大周波数。
  * `duration::Real = 0.5`: 刺激が再生される時間の長さ（秒）。
  * `Fs::Real = 44.1e3`: 刺激の周波数（Hz）。
  * `alpha_::Real = 1`: 各ビンのユニークな周波数の数を指数化する調整パラメータ。
  * `min_bins::Integer = 10`: いかなる刺激に対しても埋められる最小ビン数。
  * `max_bins::Integer = 50`: いかなる刺激に対しても埋められる最大ビン数。
  * `n_bins::Integer = 100`: 周波数範囲を分割するビンの数。
