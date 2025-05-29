```
LevenbergMarquardtState{P,T} <: AbstractGradientSolverState
```

勾配に基づく降下アルゴリズムを説明します。

# フィールド

初期化時にパラメータを省略できる場合、デフォルト値が括弧内に示されています。

  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `retraction_method::AbstractRetractionMethod`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `residual_values`: ソルバーのセットアップまたは前の反復で計算された $F$ の値
  * `residual_values_temp`: 現在の提案点の $F$ の値
  * `stop::StoppingCriterion`: 停止基準が満たされたことを示すファンクタ
  * `jacobian`: $F$ の現在のヤコビ行列
  * `gradient`: $F$ の現在の勾配
  * `step_vector`: 次の点に移動するために使用される `x` での接ベクトル
  * `last_stepsize`: `step_vector` の長さ
  * `η`: 新しい提案点を受け入れるために必要な十分なコスト減少閾値のスケーリング係数。許可される範囲: `0 < η < 1`。
  * `damping_term`: 現在のダンピング項の値
  * `damping_term_min`: ダンピング項の初期（および最小）値
  * `β`: 現在の新しい点が拒否されたときにダンピング項に掛けられるパラメータ
  * `expect_zero_residual`: true の場合、アルゴリズムは最小値での残差（目的）の値が 0 に等しいことを期待します。
  * `linear_subsolver!`: 線形部分問題 `sk .= JJ \ grad*f*c` を解く三つの引数 `sk, JJ, grad_f_c` を持つ関数。ここで `JJ` は（数値的な問題を除いて）対称正定値行列です。デフォルト値は [`default*lm*lin_solve!`](@ref) です。

# コンストラクタ

```
LevenbergMarquardtState(M, initial_residual_values, initial_jacobian; kwargs...)
```

Levenberg-Marquardt ソルバーの状態を生成します。

# キーワード引数

以下のフィールドはキーワード引数です。

  * `β=5.0`
  * `damping_term_min=0.1`
  * `η=0.2`
  * `expect_zero_residual=false`
  * `initial_gradient=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-12)`[`|`](@ref StopWhenAny)[`StopWhenStepsizeLess`](@ref)`(1e-12)`: 停止基準が満たされたことを示すファンクタ

# 参照

[`gradient_descent`](@ref), [`LevenbergMarquardt`](@ref)
