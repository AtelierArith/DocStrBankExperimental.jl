```
LevenbergMarquardtState{P,T} <: AbstractGradientSolverState
```

勾配に基づく降下アルゴリズムを説明します。

# フィールド

初期化時にパラメータを省略できる場合、デフォルト値が括弧内に示されています。

  * `x`:                     マニフォールド上の点（型 `P`）としての開始点
  * `stop`:                  （`StopAfterIteration(200) | StopWhenGradientNormLess(1e-12) | StopWhenStepsizeLess(1e-12)`）[`StoppingCriterion`](@ref)
  * `retraction_method`:     （`default_retraction_method(M, typeof(p))`）使用する再収束法、マニフォールドのデフォルト設定に従います。
  * `residual_values`       ソルバーのセットアップまたは前の反復で計算された $F$ の値
  * `residual_values_temp`  現在の提案点に対する $F$ の値
  * `jacF`                  $F$ の現在のヤコビ行列
  * `gradient`              $F$ の現在の勾配
  * `step_vector`           次の点に移動するために使用される `x` での接ベクトル
  * `last_stepsize`         `step_vector` の長さ
  * `η`                     新しい提案点を受け入れるために必要な十分なコスト減少閾値のスケーリング係数。許可される範囲: `0 < η < 1`。
  * `damping_term`          現在のダンピング項の値
  * `damping_term_min`      ダンピング項の初期（および最小）値
  * `β`                     現在の新しい点が拒否されたときにダンピング項に掛けられるパラメータ
  * `expect_zero_residual`:  （`false`）真の場合、アルゴリズムは最小値での残差（目的）の値が0に等しいことを期待します。

# コンストラクタ

```
LevenbergMarquardtState(M, initialX, initial_residual_values, initial_jacF; initial_vector), kwargs...)
```

Levenberg-Marquardtオプションを生成します。

# 参照

[`gradient_descent`](@ref), [`LevenbergMarquardt`](@ref)
