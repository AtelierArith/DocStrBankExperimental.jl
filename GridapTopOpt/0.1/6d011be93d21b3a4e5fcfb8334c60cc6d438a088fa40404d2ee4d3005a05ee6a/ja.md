```
AugmentedLagrangian(
  problem    :: PDEConstrainedFunctionals{N},
  ls_evolver :: LevelSetEvolution,
  vel_ext    :: VelocityExtension,
  φ0;
  Λ_max = 10^10, ζ = 1.1, update_mod = 5, γ = 0.1, γ_reinit = 0.5, os_γ_mult = 0.75,
  maxiter = 1000, verbose=false, constraint_names = map(i -> Symbol("C_$i"),1:N),
  converged::Function = default_al_converged, debug = false,
  has_oscillations::Function = default_has_oscillations
) where {N,O}
```

`AugmentedLagrangian`のインスタンスをいくつかの調整可能なデフォルトで作成します。

# 必要な項目

  * `problem::PDEConstrainedFunctionals`: 目的関数と制約の設定。
  * `ls_evolver::LevelSetEvolution`: 進化と再初期化方程式のソルバー。
  * `vel_ext::VelocityExtension`: 計算領域に形状感度を拡張するための速度拡張法。
  * `φ0`: FEFunctionまたはGridapDistributedの同等物として定義された初期レベルセット関数。

# オプションのデフォルト

  * `γ = 0.1`: ハミルトン・ヤコビ進化方程式を解くための時間ステップサイズの初期係数。
  * `γ_reinit = 0.5`: 再初期化方程式を解くための時間ステップサイズの係数。
  * `ζ = 1.1`: `update_mod`イテレーションごとにΛを増加させる乗数。
  * `Λ_max = 5.0`: Λの任意のエントリの最大値。
  * `update_mod = 5`: `Λ`を増加させる前のイテレーション数。
  * `reinit_mod = 1`: 再初期化方程式を解く頻度。
  * `maxiter = 1000`: アルゴリズムの最大イテレーション数。
  * `verbose=false`: 詳細表示フラグ。
  * `constraint_names = map(i -> Symbol("C_$i"),1:N)`: 履歴出力のための制約名。
  * `has_oscillations::Function = default_has_oscillations`: 履歴の振動をチェックする関数。
  * `initial_parameters::Function = default_al_init_params`: 初期λ、Λを生成する関数。これを置き換えて異なるλとΛを注入することができます。
  * `os_γ_mult = 0.75`: `has_oscillations`がtrueを返すときの`γ`の減少乗数。
  * `converged::Function = default_hp_converged`: 収束基準。
  * `debug = false`: デバッグフラグ。
