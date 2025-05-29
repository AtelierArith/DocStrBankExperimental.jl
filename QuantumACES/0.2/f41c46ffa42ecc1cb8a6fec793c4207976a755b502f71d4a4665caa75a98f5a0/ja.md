```
OptimOptions
```

[`optimise_design`](@ref) のキーワード引数、特にその中の最適化関数、勾配降下法関数 [`optimise_weights`](@ref)、繰り返し数最適化関数 [`optimise_repetitions`](@ref)、およびタプルセット最適化関数 [`optimise_tuple_set`](@ref) を含みます。

# 一般的なオプション

  * `ls_type::Symbol = :gls`: デザインを最適化するための最小二乗推定量のタイプで、`:gls`、`:wls`、または `:ols` のいずれかです。
  * `est_type::Symbol = :prod`: デザインを最適化するための推定量のタイプで、`:ordinary`、`:marginal`、`:relative`、または `:sum` または `:prod` で、`est_weight` によって重み付けされた `:ordinary` と `:relative` 推定量のメリットの算術平均または幾何平均を最適化します。
  * `est_weight::Real = 0.5`: `est_type` が `:sum` または `:prod` の場合、算術平均または幾何平均における `:ordinary` 推定量のメリットの重み付けで、`:relative` は `1 - est_weight` で重み付けされます。
  * `save_data::Bool = false`: 最適化されたデザインを自動的に保存するかどうか。

# 勾配降下法オプション

  * `learning_rate::Real = (ls_type == :ols ? 1 : 10.0^(3/4))`: 勾配降下法アルゴリズムの学習率。
  * `momentum::Real = 0.99`: 勾配降下法アルゴリズムのモーメンタム。
  * `learning_rate_scale_factor::Real = 10.0^(1/4)`: 勾配降下法アルゴリズムがメリットを減少させる方向に繰り返しステップを踏む場合に学習率を減少させるための係数。
  * `max_steps::Integer = 1000`: 勾配降下法の最大ステップ数。
  * `convergence_threshold::Real = 1e-5`: 勾配降下法アルゴリズムの収束閾値。
  * `convergence_steps::Integer = 5`: 収束を確認するためのステップ数。
  * `grad_diagnostics::Bool = false`: 勾配降下法の診断を表示するかどうか。

# 繰り返し数最適化オプション

  * `rep_est_type::Symbol = :relative`: 繰り返し数を最適化するための推定量のタイプで、`:ordinary`、`:marginal`、`:relative`、または `:sum` または `:prod` で、`rep_est_weight` によって重み付けされた `:ordinary` と `:relative` 推定量のメリットの算術平均または幾何平均を最適化します。
  * `rep_est_weight::Real = 0.5`: `rep_est_type` が `:sum` または `:prod` の場合、算術平均または幾何平均における `:ordinary` 推定量のメリットの重み付けで、`:relative` は `1 - rep_est_weight` で重み付けされます。
  * `error_target::Real = 0.1`: 繰り返し数の初期化を制御し、この誤差率を大まかにターゲットにします。これを `0` に設定すると、繰り返し数は 0 に初期化され、すべての繰り返し数は最適化前に 2 に設定されます。
  * `add_circuit::Bool = true`: 繰り返しタプルセットに回路自体を追加するかどうか。
  * `cycle_convergence_threshold::Real = 1e-5`: 繰り返し数を最適化するための循環座標降下アルゴリズムの収束閾値。
  * `convergence_cycles::Integer = 5`: 繰り返し数を最適化するための循環座標降下アルゴリズムの収束を確認するためのステップ数。
  * `min_depth::Integer = 0`: 繰り返しタプルの最小深さ。
  * `max_depth::Integer = 1000`: 繰り返しタプルの最大深さ。
  * `max_cycles::Integer = 100`: 繰り返し数を最適化するための循環座標降下アルゴリズムで使用する最大サイクル数。
  * `repeat_points::Integer = 1`: 各繰り返し数は、最小の繰り返し数を `initial_shrink_factor` で縮小したものと対数的に間隔を空けた `repeat_points` の繰り返し数を持つように増強されます。
  * `initial_shrink_factor::Real = 2^(repeat_points - 1)`: 増強されたタプルセットの最小繰り返し数を縮小するための係数。
  * `rep_diagnostics::Bool = true`: 繰り返し数最適化の診断を表示するかどうか。

# タプルセット最適化オプション

  * `tuple_est_type::Symbol = :ordinary`: タプルセットを最適化するための推定量のタイプで、`:ordinary`、`:marginal`、`:relative`、`:sum`、または `:prod` で、`tuple_est_weight` によって重み付けされた `:ordinary` と `:relative` 推定量のメリットの算術平均または幾何平均を最適化します。
  * `tuple_est_weight::Real = 0.5`: `tuple_est_type` が `:sum` または `:prod` の場合、算術平均または幾何平均における `:ordinary` 推定量のメリットの重み付けで、`:relative` は `1 - tuple_est_weight` で重み付けされます。
  * `max_excursions::Integer = 100`: タプルセットを最適化するために使用されるエクスカーションの数。
  * `excursions_unchanged::Integer = 3`: 最適化ルーチンが終了する前にタプルセットを変更しないエクスカーションの数。
  * `excursion_length::Integer = 5`: 各エクスカーションによって追加されるタプルの数。
  * `extra_tuple_number::Integer = 5`: 基本タプルセットの数を超えて、タプルセット最適化手順によって追加されるタプルの数。
  * `max_tuple_length::Integer = 20`: ランダムタプルの最大長。
  * `tuple_length_zipf_power::Real = 1`: ランダムタプルの長さをZipf的に選択する際に使用するZipfのべき乗。
  * `repeat_zipf_powers::Vector{Float64} = [Inf; 2.0]`: ランダムタプルの生成中にランダムに追加されるエントリを何回繰り返すかをZipf的に選択する際に、ベクトルから均等にランダムに選ばれるZipfのべき乗。
  * `mirror_values::Vector{Bool} = [false; true]`: ランダムタプルを生成する際にタプルをミラーリングするかどうかを、ベクトルから均等にランダムに選択します。
  * `trial_factor::Integer = 20`: エクスカーションがタプルセットを成長させるために追加する必要がある各タプルのために試行されるランダムタプルの数。
  * `grow_greedy::Bool = true`: エクスカーションがメリットに従って貪欲にタプルをセットに追加するか、メリットを減少させても追加するか。
  * `weight_experiments::Bool = false`: タプルのショットの重みをそのタプルの実験数で重み付けするかどうか。通常は `true` ですが、`false` の方がタプルセット最適化には効果的です。
  * `seed::Union{UInt64, Nothing} = nothing`: ランダムにタプルを生成するために使用されるシード。
  * `tuple_diagnostics::Bool = true`: タプルセット最適化の診断を表示するかどうか。
