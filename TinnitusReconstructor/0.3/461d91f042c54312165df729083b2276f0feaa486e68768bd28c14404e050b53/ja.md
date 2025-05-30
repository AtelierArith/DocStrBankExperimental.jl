```
Brimijoin(; kwargs...) <: BinnedStimgen
```

各トノトピックビンが、等間隔のリストからの振幅値で等しい確率で満たされる刺激生成タイプ。

# キーワード

  * `min_freq::Real = 100`: サンプリングする範囲の最小周波数。
  * `max_freq::Real = 22e3`: サンプリングする範囲の最大周波数。
  * `duration::Real = 0.5`: 刺激が再生される時間の長さ（秒）。
  * `Fs::Real = 44.1e3`: 刺激の周波数（Hz）。
  * `amp_min::Real = -20`: ビンが持つことができる最も低いdB値。
  * `amp_max::Real = 0`: ビンが持つことができる最も高いdB値。
  * `amp_step::Int = 6`: `amp_min`と`amp_max`の間の均等に間隔を空けたステップの数。
  * `n_bins::Integer = 100`: 周波数範囲を分割するビンの数。
