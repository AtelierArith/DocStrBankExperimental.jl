```
PowerDistribution(; kwargs...) <: BinnedStimgen
```

各ビンの周波数が耳鳴りの例から学習したパワー分布からサンプリングされる刺激生成タイプ。

# キーワード

  * `min_freq::Real = 100`: サンプリングする範囲の最小周波数。
  * `max_freq::Real = 22e3`: サンプリングする範囲の最大周波数。
  * `duration::Real = 0.5`: 刺激が再生される時間の長さ（秒）。
  * `Fs::Real = 44.1e3`: 刺激の周波数（Hz）。
  * `n_bins::Integer = 100`: 周波数範囲を分割するビンの数。
  * `distribution_filepath::AbstractString=joinpath(@__DIR__, "distribution.csv")`: 刺激が生成されるデフォルトのパワー分布へのファイルパス。
