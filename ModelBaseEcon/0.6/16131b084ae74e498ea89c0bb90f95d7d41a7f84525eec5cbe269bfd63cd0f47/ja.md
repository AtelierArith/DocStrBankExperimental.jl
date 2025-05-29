```
eval_equation(model::AbstractModel, eqn::AbstractEquation, sim_data::AbstractMatrix{Float64}, rng::UnitRange{Int64} = 1:size(sim_data,1))
```

与えられた方程式の残差を時間の範囲にわたって評価します。

この関数は、シミュレーションデータ `sim_data` の範囲 `rng` の各時間ステップに対して、提供された方程式 `eqn` の残差を計算します。評価中はモデルのラグとリードの構造が尊重されます。

# 引数

  * `model::AbstractModel`: 評価される方程式を含むモデル。
  * `eqn::AbstractEquation`: 残差を計算するための方程式。
  * `sim_data::AbstractMatrix{Float64}`: シミュレーションデータで、行は時間点を、列はモデルの全変数（変数、ショック、補助変数）を表します。
  * `rng::UnitRange{Int64}`: 方程式を評価する時間点の範囲。デフォルトでは、`sim_data` のすべての時間点にわたって評価します。

# 戻り値

  * `res::Vector{Float64}`: 範囲 `rng` の各時間点に対する残差のベクトル。残差を計算できない時間点（不十分なラグまたはリードのため）のエントリは `NaN` で埋められます。
