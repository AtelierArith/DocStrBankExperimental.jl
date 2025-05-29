```
SchwarzAlgorithm{GT<:Plasmo.AbstractOptiGraph}
```

分割されたグラフに適用されるシュワルツに基づく最適化アルゴリズムを表します。

フィールド:

  * `graph::GT`: アルゴリズムに渡されるグローバル最適化グラフ。
  * `subproblems::Vector{GT}`: （拡張された）サブプロブレムを表すサブグラフのリスト。
  * `element_subproblem_map::Dict{Plasmo.OptiElement,GT}`: グラフ内の要素をそれに関連するサブプロブレムにマッピングします。
  * `objective_func::Plasmo.AbstractJuMPScalar`: グラフのためのグローバル目的関数。
  * `options::Options`: アルゴリズムの設定オプション。
  * `initialized::Bool`: アルゴリズムが初期化されているかどうか。
  * `status::MOI.TerminationStatusCode`: アルゴリズムの現在のステータス。
  * `err_pr::Union{Nothing,Float64}`: 現在のプライマルエラー。
  * `err_du::Union{Nothing,Float64}`: 現在のデュアルエラー。
  * `objective_value::Union{Nothing,Float64}`: 現在の目的値。
  * `iteration::Int64`: 現在のイテレーションカウント。
  * `primal_error_iters::Vector{Float64}`: イテレーションごとのプライマルエラーの履歴。
  * `dual_error_iters::Vector{Float64}`: イテレーションごとのデュアルエラーの履歴。
  * `objective_iters::Vector{Float64}`: イテレーションごとの目的値の履歴。
  * `solve_time::Float64`: 合計解決時間。
  * `timers::Timers`: パフォーマンス指標を測定するためのタイマー。
