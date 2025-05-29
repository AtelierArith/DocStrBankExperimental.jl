```
pmc_abc(model::Models.AbstractTimescaleModel; epsilon_0=1.0, max_iter=10000, min_accepted=100, steps=10, sample_only=false, minAccRate=0.01, target_acc_rate=0.01)
```

人口モンテカルロ近似ベイズ計算（PMC-ABC）推論を実行します。

# 引数

  * `model::Models.AbstractTimescaleModel`: 推論を行うモデル
  * `epsilon_0::Float64=1.0`: 受け入れのための初期エプシロン閾値
  * `max_iter::Int=10000`: ステップごとの最大反復回数
  * `min_accepted::Int=100`: 必要な受け入れサンプルの最小数
  * `steps::Int=10`: 実行するPMCステップの数
  * `sample_only::Bool=false`: trueの場合、適応なしでサンプリングのみを実行
  * `minAccRate::Float64=0.01`: 停止前の最小受け入れ率
  * `target_acc_rate::Float64=0.01`: エプシロン適応のための目標受け入れ率

# 戻り値

各PMCステップの結果を含むNamedTuplesのベクター：

  * 受け入れられたパラメータ（theta_accepted）
  * 距離（D_accepted）
  * 受け入れ/総サンプル数
  * エプシロン閾値
  * サンプル重み
  * 共分散行列（tau_squared）
  * 有効サンプルサイズ
