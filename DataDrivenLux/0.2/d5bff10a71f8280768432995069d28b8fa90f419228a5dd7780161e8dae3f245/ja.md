```julia
struct Candidate{__T_rng<:Random.AbstractRNG, __T_st<:NamedTuple, __T_ps<:(AbstractVector), __T_incoming_path<:(Vector{<:DataDrivenLux.AbstractPathState}), __T_outgoing_path<:(Vector{<:DataDrivenLux.AbstractPathState}), __T_statistics<:DataDrivenLux.PathStatistics, __T_observed<:DataDrivenLux.ObservedModel, __T_parameterdist<:DataDrivenLux.ParameterDistributions, __T_scales<:(AbstractVector), __T_parameters<:(AbstractVector), __T_model<:DataDrivenLux.ComponentModel} <: StatsAPI.StatisticalModel
```

現在の候補解の情報を保持するコンテナです。

# フィールド

  * `rng`: ランダムシード
  * `st`: 現在の状態
  * `ps`: 現在のパラメータ
  * `incoming_path`: 入力パス
  * `outgoing_path`: 出力パス
  * `statistics`: 統計
  * `observed`: 観測モデル
  * `parameterdist`: パラメータ分布
  * `scales`: 最適スケール
  * `parameters`: 最適パラメータ
  * `model`: コンポーネントモデル
