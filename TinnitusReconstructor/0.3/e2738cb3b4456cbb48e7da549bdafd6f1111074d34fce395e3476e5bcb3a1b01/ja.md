```
UniformPrior(; kwargs...) <: BinnedStimgen
```

刺激生成タイプで、充填されたビンの数は、区間 `[min_bins, max_bins]` の一様分布から選択されます。

# キーワード

  * `min_freq::Real = 100`: サンプリングする範囲の最小周波数。
  * `max_freq::Real = 22e3`: サンプリングする範囲の最大周波数。
  * `duration::Real = 0.5`: 刺激が再生される時間の長さ（秒）。
  * `Fs::Real = 44.1e3`: 刺激の周波数（Hz）。
  * `min_bins::Integer = 10`: いかなる刺激でも充填される可能性のある最小ビン数。
  * `max_bins::Integer = 50`: いかなる刺激でも充填される可能性のある最大ビン数。
  * `n_bins::Integer = 100`: 周波数範囲を分割するビンの数。
