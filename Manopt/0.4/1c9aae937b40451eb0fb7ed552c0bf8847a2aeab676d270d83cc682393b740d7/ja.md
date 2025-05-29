```
ConvexBundleMethodState <: AbstractManoptSolverState
```

[`convex_bundle_method`](@ref) ソルバーのオプション値を格納します。

# フィールド

  * `atol_λ`:                    （`eps()`）λの凸係数に対する許容誤差パラメータ
  * `atol_errors`:               （`eps()`）線形化誤差に対する許容誤差パラメータ
  * `bundle`:                    各反復とその反復で計算された部分勾配を収集するバンドル
  * `bundle_cap`:                （`25`）バンドルが記憶できる要素の最大数
  * `diameter`:                  （`50.0`）開始点における目的関数のレベルセットの直径の推定値
  * `domain`:                    （`(M, p) -> isfinite(f(M, p))`）現在の候補が目的関数 `f` の定義域にあるときに真を返す関数。例えば `domain = (M, p) -> p ∈ dom f(M, p) ? true : false`
  * `g`:                         降下方向
  * `inverse_retraction_method`: 使用する逆リトラクション
  * `k_max`:                     多様体の断面曲率の上限
  * `linearization_errors`:      最後の真剣なステップでの線形化誤差
  * `m`:                         （`1e-3`）コストの減少をテストするためのパラメータ：$f(q_{k+1}) \le f(p_k) + m \xi$。
  * `p`:                         現在の候補点
  * `p_last_serious`:            最後の真剣な反復
  * `retraction_method`:         使用するリトラクション
  * `stop`:                      [`StoppingCriterion`](@ref)
  * `transported_subgradients`:  `p_last_serious` に輸送されたバンドルの部分勾配
  * `vector_transport_method`:   使用するベクトル輸送法
  * `X`:                         （`zero_vector(M, p)`）最後に評価された `p` における可能な部分勾配からの現在の要素。
  * `stepsize`:                  （[`ConstantStepsize`](@ref)`(M)`）[`Stepsize`](@ref)
  * `ε`:                         線形化誤差の凸結合
  * `λ`:                         サブ問題を解く凸係数
  * `ξ`:                         $ξ = -\lvert g\rvert^2 – ε$ によって与えられる停止パラメータ
  * `sub_problem`:               （[`convex_bundle_method_subsolver`]) 最後の真剣な反復 `p_last_serious`、線形化誤差 `linearization_errors`、および輸送された部分勾配 `transported_subgradients` を考慮して `M` 上のサブ問題を解く関数、
  * `sub_state`:                 サブソルバーのための [`AbstractManoptSolverState`](@ref)

# コンストラクタ

```
ConvexBundleMethodState(M::AbstractManifold, p; kwargs...)
```

`p_last_serious` を除くすべてのフィールドのデフォルトを持つキーワードを使用します。`p_last_serious` は `p` と同じ型を取得します。例えば、使用する接ベクトルの型を指定するために `X=` を使用できます。
