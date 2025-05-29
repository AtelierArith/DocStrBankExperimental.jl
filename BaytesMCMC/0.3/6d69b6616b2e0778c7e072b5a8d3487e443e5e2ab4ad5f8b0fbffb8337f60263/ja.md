```julia
struct ConfigHMC{K<:BaytesMCMC.KineticEnergy, S<:BaytesMCMC.ConfigStepnumber} <: BaytesCore.AbstractConfiguration
```

HMCサンプラーのデフォルト設定。

# フィールド

  * `δ::Float64`: 目標受容率
  * `window::BaytesMCMC.ConfigTuningWindow`: 各サイクルでの調整反復のデフォルトサイズ。
  * `energy::BaytesMCMC.KineticEnergy`: ハミルトニアンで使用される運動エネルギー: GaussianKineticEnergy
  * `stepnumber::BaytesMCMC.ConfigStepnumber`: ステップ番号の適応
  * `difforder::BaytesDiff.DiffOrderOne`: 提案ステップを実行するために必要な目的関数の微分可能な順序
