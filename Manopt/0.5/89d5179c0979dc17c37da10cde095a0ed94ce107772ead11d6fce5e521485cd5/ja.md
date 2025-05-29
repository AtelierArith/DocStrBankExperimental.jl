```
ConvexBundleMethodState <: AbstractManoptSolverState
```

[`convex_bundle_method`](@ref) ソルバーのオプション値を格納します。

# フィールド

以下のフィールドは、（実数）型 `R`、点の型 `P`、および接ベクトルの型 `T` を必要とします。

  * `atol_λ::R`:                 λ における凸係数の許容誤差パラメータ
  * `atol_errors::R`:            線形化誤差の許容誤差パラメータ
  * `bundle<:AbstractVector{Tuple{<:P,<:T}}`: 各反復とその反復で計算された部分勾配を収集するバンドル
  * `bundle_cap::Int`:           バンドルが記憶できる要素の最大数
  * `diameter::R`:               開始点における目的関数のレベルセットの直径の推定値
  * `domain: f の定義域`(M,p) -> b`現在の候補が`f` の定義域にあるときに真を返し、そうでない場合は偽を返します。
  * `g::T`:                      降下方向
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `k_max::R`:                  多様体の断面曲率の上限
  * `linearization_errors<:AbstractVector{<:R}`: 最後の真剣なステップでの線形化誤差
  * `m::R`:                      コストの減少をテストするためのパラメータ: $f(q_{k+1}) ≤ f(p_k) + m ξ$。
  * `p::P`:                      現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `p_last_serious::P`:         最後の真剣な反復
  * `retraction_method::AbstractRetractionMethod`: 使用する引き戻し $\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `transported_subgradients`:  `p_last_serious` に輸送されたバンドルの部分勾配
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照
  * `X::T`:                      現在の反復での部分勾配を格納する多様体 $\mathcal M$ 上の点 $p$ での接ベクトル
  * `stepsize::Stepsize`:        ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `ε::R`:                      線形化誤差の凸結合
  * `λ:::AbstractVector{<:R}`:   サブ問題の解からの凸係数
  * `ξ`:                         $ξ = -\lVert g\rvert^2 – ε$ で与えられる停止パラメータ
  * `sub_problem::Union{AbstractManoptProblem, F}`: ソルバー用の問題またはクローズドフォームの解関数を指定します。これは、割り当て可能またはインプレースである可能性があります。
  * `sub_state::Union{AbstractManoptProblem, F}`: 使用するサブソルバーを指定するための状態。クローズドフォームの解の場合、これは関数の型を示します。

# コンストラクタ

```
ConvexBundleMethodState(M::AbstractManifold, sub_problem, sub_state; kwargs...)
ConvexBundleMethodState(M::AbstractManifold, sub_problem=convex_bundle_method_subsolver; evaluation=AllocatingEvaluation(), kwargs...)
```

多様体 `M` 上の [`convex_bundle_method`](@ref) の状態を生成します。

## 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `sub_problem`: ソルバー用の問題またはクローズドフォームの解関数を指定します。これは、割り当て可能またはインプレースである可能性があります。
  * `sub_state`: 使用するサブソルバーを指定するための状態。クローズドフォームの解の場合、これは関数の型を示します。

# キーワード引数

以下のキーワード引数のほとんどは、前述のフィールドのデフォルト値を設定します。

  * `atol_λ=eps()`
  * `atol_errors=eps()`
  * `bundle_cap=25``
  * `m=1e-2`
  * `diameter=50.0`
  * `domain=(M, p) -> isfinite(f(M, p))`
  * `k_max=0`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体 $\mathcal M$ 上の点
  * `stepsize=`[`default_stepsize`](@ref)`(M, ConvexBundleMethodState)`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stopping_criterion=`[`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8)`[`|`](@ref StopWhenAny)[`StopAfterIteration`](@ref)`(5000)`: 停止基準が満たされていることを示すファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)` 使用する接ベクトルの型を指定します。
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照

```
