```
ProximalBundleMethodState <: AbstractManoptSolverState
```

は [`proximal_bundle_method`](@ref) ソルバーのオプション値を格納します。

# フィールド

  * `approx_errors`:            最後の真剣なステップでの線形化誤差の近似
  * `bundle`:                   各反復とその反復で計算された部分勾配を集めるバンドル
  * `bundle_size`:              （`50`）バンドルの最大サイズ
  * `c`:                         近似誤差の凸結合
  * `d`:                         降下方向
  * `inverse_retraction_method`: 内部で使用する逆引き戻し
  * `m`:                         （`0.0125`）コストの減少をテストするためのパラメータ
  * `p`:                         現在の候補点
  * `p_last_serious`:            最後の真剣な反復
  * `retraction_method`:         内部で使用する引き戻し
  * `stop`:                      [`StoppingCriterion`](@ref)
  * `transported_subgradients`:  `p_last_serious` に輸送されたバンドルの部分勾配
  * `vector_transport_method`:   内部で使用するベクトル輸送法
  * `X`:                         （`zero_vector(M, p)`）最後に評価された `p` における可能な部分勾配からの現在の要素。
  * `α₀`:                        （`1.2`）`α` の初期化値で、`η` を更新するために使用される
  * `α`:                         曲率依存のパラメータで、`η` を更新するために使用される
  * `ε`:                         （`1e-2`）多様体の単射半径に関連するステップサイズのようなパラメータ
  * `δ`:                         `μ` を更新するためのパラメータ：もし $δ < 0$ なら $μ = \log(i + 1)$、そうでなければ $μ += δ μ$
  * `η`:                         近似誤差を更新するための曲率依存の項
  * `λ`:                         サブ問題を解くための凸係数
  * `μ`:                         （`0.5`）サブ問題の（初期）近接パラメータ
  * `ν`:                         $ν = - μ |d|^2 - c$ で与えられる停止パラメータ
  * `sub_problem`:               最後の真剣な反復 `p_last_serious`、線形化誤差 `linearization_errors`、および輸送された部分勾配 `transported_subgradients` を考慮してサブ問題を解決する新しい割り当てで評価する関数
  * `sub_state`:                 サブソルバーのための [`AbstractManoptSolverState`](@ref)

# コンストラクタ

```
ProximalBundleMethodState(M::AbstractManifold, p; kwargs...)
```

は、`p_last_serious` を除くすべてのフィールドのキーワードを持ち、`p` と同じ型を取得します。例えば、使用する接ベクトルの型を指定するために `X=` を使用できます。
