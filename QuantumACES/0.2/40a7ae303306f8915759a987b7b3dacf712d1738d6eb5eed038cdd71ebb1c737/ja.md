```
simulate_aces(d::Design, budget_set::Vector{Int}; kwargs...)
```

シミュレートされた ACES ノイズ特性実験結果を [`ACESData`](@ref) オブジェクトとして返します。これは、実験デザイン `d` に対して `budget_set` 内の各測定予算にわたって行われます。

警告: シードは Stim と同じ機能を持っています。同じランダムシードの動作は、Stim の異なるバージョン間で異なります。また、測定ショットがバッチでサンプリングされる場合（`max_samples` を超えた場合）、すべてのショットが一度にサンプリングされる場合とは結果が異なります。

# 引数

  * `d::Design`: 実験デザイン。
  * `budget_set::Vector{Int}`: ACES をシミュレートするための測定予算。

# キーワード引数

  * `repetitions::Integer = 1`: シミュレーションの繰り返し回数。
  * `seed::Union{UInt64, Nothing} = nothing`: ランダム数生成に使用するシード。
  * `N_warn::Integer = 10^5`: 特定のキーワード引数の選択についてユーザーに警告する回路固有値の数。
  * `max_samples::Integer = 10^9`: 単一のシミュレーションで収集される Stim サンプルの最大数。
  * `min_eigenvalue::Real = 0.1`: この閾値未満の回路固有値は推定手続きから省略されます。
  * `clip_warning::Bool = false`: 切り取られた固有値についてユーザーに警告するかどうか。
  * `N_warn_split::Integer = 5 * 10^3`: `split` が false の場合にユーザーに警告する回路固有値の数。
  * `split::Bool = (d.c.gate_data.N < N_warn_split ? false : true)`: ゲート固有値の投影をゲート間で分割するか、すべてのゲート固有値を同時に投影するか。
  * `precision::Real = 1e-8`: ノイズ推定を確率シンプレックスに投影するためのソルバーの精度。
  * `diagnostics::Bool = true`: 診断を印刷するかどうか。
  * `detailed_diagnostics::Bool = false`: Stim シミュレーションの詳細な診断を印刷するかどうか。
  * `save_data::Bool = false`: データを保存するかどうか。
  * `save_interval::Integer = 50`: データを保存する繰り返し間隔。
  * `clear_design::Bool = false`: フルシミュレーションデータを保存した後に保存されたデザインデータをクリアするかどうか。

```
