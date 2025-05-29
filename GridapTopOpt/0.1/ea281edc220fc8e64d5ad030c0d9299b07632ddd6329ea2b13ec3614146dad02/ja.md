```
HilbertianProjection(
  problem :: PDEConstrainedFunctionals{N},
  ls_evolver :: LevelSetEvolution,
  vel_ext :: VelocityExtension,
  φ0;
  orthog = HPModifiedGramSchmidt(),
  λ=0.5, α_min=0.1, α_max=1.0, γ=0.1, γ_reinit=0.5,
  ls_max_iters = 10, ls_δ_inc = 1.1, ls_δ_dec = 0.7,
  ls_ξ = 0.0025, ls_ξ_reduce_coef = 0.1, ls_ξ_reduce_abs_tol = 0.01,
  ls_γ_min = 0.001, ls_γ_max = 0.1,
  maxiter = 1000, verbose=false, constraint_names = map(i -> Symbol("C_$i"),1:N),
  converged::Function = default_hp_converged, debug = false
) where {N}
```

`HilbertianProjection`のインスタンスを作成し、直交化手法を含むいくつかの調整可能なデフォルトを設定します。デフォルトでは、後者は[`HPModifiedGramSchmidt`](@ref)です。

# 必要なもの

  * `problem::PDEConstrainedFunctionals{N}`: 目的と制約の設定。
  * `ls_evolver::LevelSetEvolution`: 進化と再初期化方程式のソルバー。
  * `vel_ext::VelocityExtension`: 形状感度を計算ドメインに拡張するための速度拡張法。
  * `φ0`: FEFunctionまたはGridapDistributedの同等物として定義された初期レベルセット関数。

# アルゴリズムのデフォルト

  * `γ = 0.1`: ハミルトン-ヤコビ進化方程式を解くための時間ステップサイズの初期係数。
  * `γ_reinit = 0.5`: 再初期化方程式を解くための時間ステップサイズの係数。
  * `maxiter = 1000`: アルゴリズムの最大反復回数。
  * `verbose=false`: 詳細表示フラグ。
  * `constraint_names = map(i -> Symbol("C_$i"),1:N)`: 履歴出力のための制約名。
  * `converged::Function = default_hp_converged`: 収束基準。
  * `has_oscillations::Function = (ls_enabled ? (args...)->false : default_has_oscillations`: デフォルトでは、ラインサーチが有効な場合は無効になります。
  * `os_γ_mult = 0.5`: `has_oscillations`がtrueを返すときの`γ`の減少乗数。
  * `debug = false`: デバッグフラグ。
  * `α_min ∈ [0,1] = 0.1`: 投影された目的の降下係数の下限を制御します。`α_min = 1`は目的関数を無視し、代わりに制約満足問題を解決します。
  * `α_max ∈ [0,1] = 1.0`: 投影された目的の降下係数の上限を制御します。通常、最適解に「遅く」近づくことを望まない限り、これを変更するべきではありません。
  * `λ = 0.5`: 制約の減少率。

実際には、通常`α_min`のみを調整して、目的と制約の改善のバランスを制御します。

# ラインサーチのデフォルト

  * `ls_enabled = true`: ラインサーチが使用されるかどうかを設定します。
  * `ls_max_iters = 10`: ラインサーチの最大反復回数。
  * `ls_δ_inc = 1.1`: 受け入れ時の`γ`の増加乗数。
  * `ls_δ_dec = 0.7`: 拒否時の`γ`の減少乗数。
  * `ls_ξ = 1.0`: 目的の削減に対するラインサーチの許容範囲。
  * `ls_ξ_reduce_coef = 0.0025`: 許容範囲内の制約がある場合の`ls_ξ`の係数（以下参照）。
  * `ls_ξ_reduce_abs_tol = 0.01`: `ls_ξ`を`ls_ξ_reduce_coef`を介して減少させるための制約の許容範囲。
  * `ls_γ_min = 0.001`: ハミルトン-ヤコビ進化方程式を解くための時間ステップサイズの最小係数。
  * `ls_γ_max = 0.1`: ハミルトン-ヤコビ進化方程式を解くための時間ステップサイズの最大係数。

境界のより保守的な進化は、`ls_γ_max`を減少させることで達成できます。

!!! note
    ラインサーチは、制約が設定された許容範囲内にあるときのみ強制されるように調整されています。これは、特に制約が飽和から遠く、目的が制約を改善するために減少しなければならない問題に対して、一般的により良い最適化履歴をもたらします。

    これは、`ls_ξ = 0.0025`および`ls_ξ_reduce_coef = 0.1`を取ることで常に強制されるように設定できます。

