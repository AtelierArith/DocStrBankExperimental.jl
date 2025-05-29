```
basic_abc(model::Models.AbstractTimescaleModel; kwargs...)
```

基本的なABC拒否サンプリングを実行します。

# 引数

  * `model::Models.AbstractTimescaleModel`: 推論を行うモデル
  * `epsilon::Float64`: 受け入れ閾値
  * `max_iter::Integer`: 最大反復回数
  * `min_accepted::Integer`: 必要な受け入れサンプルの最小数
  * `pmc_mode::Bool=false`: PMC提案分布を使用するかどうか
  * `weights=Array{Float64}`: 重要度重み（PMCモードで使用）
  * `theta_prev=Array{Float64}`: 前のパラメータ（PMCモードで使用）
  * `tau_squared=Array{Float64}`: 共分散行列（PMCモードで使用）
  * `show_progress::Bool=true`: 進行状況バーを表示するかどうか

# 戻り値

次の内容を含むNamedTuple:

  * `samples`: 提案されたすべてのパラメータ
  * `isaccepted`: 受け入れられたサンプルのブールマスク
  * `theta_accepted`: 受け入れられたパラメータ
  * `distances`: すべての提案の距離
  * `n_accepted`: 受け入れられたサンプルの数
  * `n_total`: 総反復回数
  * `epsilon`: 使用された受け入れ閾値
  * `weights`: サンプル重み（基本的なABCでは均一）
  * `tau_squared`: 共分散行列（基本的なABCではゼロ）
  * `eff_sample`: 有効サンプルサイズ
