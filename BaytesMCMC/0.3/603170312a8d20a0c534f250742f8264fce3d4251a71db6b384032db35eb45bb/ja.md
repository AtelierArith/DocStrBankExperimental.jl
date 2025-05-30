```julia
struct ConfigTuningWindow
```

各サイクルのチューニング反復のためのデフォルト設定。

# フィールド

  * `window::Vector{Int64}`: MCMCフェーズチューニングウィンドウの長さ、すなわち: 5 = フェーズ名の2番目のウィンドウの5回の繰り返し
  * `buffer::Vector{Int64}`: (増加する) ウィンドウの長さ、すなわち: window=3の場合、buffer=10 -> 合計ウィンドウの長さ: 10-20-30
  * `phasenames::Vector{BaytesMCMC.SamplingPhase}`: フェーズ名の名前、現在サポートされているもの: Warmup(), Adaptionˢˡᵒʷ(), Adaptionᶠᵃˢᵗ(), Exploration()
