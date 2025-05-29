```
GaussianNoiseNoBins(; kwargs...) <: Stimgen
```

各周波数の振幅がガウス分布に従って選ばれる刺激生成タイプです。

# キーワード

  * `min_freq::Real = 100`: サンプリングする範囲の最小周波数。
  * `max_freq::Real = 22e3`: サンプリングする範囲の最大周波数。
  * `duration::Real = 0.5`: 刺激が再生される時間の長さ（秒）。
  * `Fs::Real = 44.1e3`: 刺激の周波数（Hz）。
  * `amplitude_mean::Real = -10`: ガウスの平均。
  * `amplitude_var::Real = 3`: ガウスの分散。
