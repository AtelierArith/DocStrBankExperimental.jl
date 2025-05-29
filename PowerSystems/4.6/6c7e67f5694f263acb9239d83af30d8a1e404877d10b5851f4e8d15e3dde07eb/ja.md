強制的な停止に関する情報を含む属性で、遷移確率は幾何分布でモデル化されています。停止確率と回復確率は時系列としてモデル化できます。

# 引数

  * `time_to_recovery::Int`: 障害発生後の回復までの経過時間（ミリ秒単位）。
  * `outage_transition_probability::Float64`: 幾何分布における故障の確率（1 - p）を特徴付けます。
  * `internal::InfrastructureSystemsInternal`: 電力システムの内部参照、変更しないでください。
