```julia
struct ConfigNUTS{K<:BaytesMCMC.KineticEnergy} <: BaytesCore.AbstractConfiguration
```

NUTSサンプラーのデフォルト設定。

# フィールド

  * `δ::Float64`: 目標受け入れ率
  * `max_depth::Int64`: 最大ツリー深度。
  * `window::BaytesMCMC.ConfigTuningWindow`: 各サイクルのチューニング反復のデフォルトサイズ。
  * `energy::BaytesMCMC.KineticEnergy`: ハミルトニアンで使用される運動エネルギー: GaussianKineticEnergy
  * `difforder::BaytesDiff.DiffOrderOne`: 提案ステップを実行するために必要な目的関数の微分可能な順序
