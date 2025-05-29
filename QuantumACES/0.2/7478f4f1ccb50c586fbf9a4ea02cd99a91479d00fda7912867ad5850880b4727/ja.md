```
generate_rand_design(d::Design, randomisations::Vector{Int}, shot_budget::Integer, experiment_shots::Integer; kwargs...)
generate_rand_design(d::Design, min_randomisations::Integer, target_shot_budget::Integer, experiment_shots::Integer; kwargs...)
```

`d`のためのパウリフレームランダム化実験アンサンブルを記述する[`RandDesign`](@ref)オブジェクトを返します。[`get_randomisations`](@ref)によって出力されたランダム化の数`randomisations`とショット予算`shot_budget`、および各実験のショット数`experiment_shots`のいずれかを供給するか、またはその関数の引数、すなわち各タプルの最小ランダム化数`min_randomisations`、ターゲットショット予算`target_shot_budget`、および各実験のショット数`experiment_shots`を指定します。

# 引数

  * `d::Design`: 実験デザイン。
  * `randomisations::Vector{Int}`: デザイン内の各タプルのためのランダム化の数。
  * `shot_budget::Integer`: ランダム化された実験アンサンブルのショット予算。
  * `min_randomisations::Integer`: デザイン内の各タプルのための最小ランダム化数。
  * `target_shot_budget::Integer`: ランダム化された実験アンサンブルのターゲットショット予算。
  * `experiment_shots::Integer`: ランダム化された実験アンサンブル内の各実験のためのショット数。

# キーワード引数

  * `job_circuit_number::Integer = 200`: 各ジョブ内の回路の数。
  * `seed::Union{UInt64, Nothing} = nothing`: ランダム化のためのランダムシード。
  * `diagnostics::Bool = false`: 診断を印刷するかどうか。
  * `save_data::Bool = false`: ランダム化されたデザインを保存するかどうか。
