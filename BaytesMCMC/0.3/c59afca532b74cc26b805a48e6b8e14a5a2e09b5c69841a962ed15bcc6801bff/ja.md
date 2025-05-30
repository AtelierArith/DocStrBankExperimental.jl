```julia
struct ConfigMALA <: BaytesCore.AbstractConfiguration
```

MALAサンプラーのデフォルト設定。

# フィールド

  * `δ::Float64`: 目標受け入れ率
  * `window::BaytesMCMC.ConfigTuningWindow`: 各サイクルの調整反復のデフォルトサイズ。
  * `difforder::BaytesDiff.DiffOrderOne`: 提案ステップを実行するために必要な目的関数の微分可能な順序。
