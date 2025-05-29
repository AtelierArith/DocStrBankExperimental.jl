```
ProximalBundleMethodState <: AbstractManoptSolverState
```

は [`proximal_bundle_method`](@ref) ソルバーのオプション値を格納します。

# フィールド

  * `α`:                        `η` を更新するために使用される曲率依存パラメータ
  * `α₀`:                       `η` を更新するために使用される `α` の初期化値
  * `approx_errors`:            最後の真剣なステップでの線形化誤差の近似
  * `bundle`:                   各反復とその反復で計算された部分勾配を収集するバンドル
  * `bundle_size`:              バンドルの最大サイズ
  * `c`:                        近似誤差の凸結合
  * `d`:                        降下方向
  * `δ`:                        `μ` を更新するためのパラメータ: $δ < 0$ の場合は $μ = \log(i + 1)$、それ以外の場合は $μ += δ μ$
  * `ε`:                        多様体の単射半径に関連するステップサイズのようなパラメータ
  * `η`:                        近似誤差を更新するための曲率依存項
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆再収縮 $\operatorname{retr}^{-1}$、詳細は [再収縮とその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `λ`:                        サブ問題を解くための凸係数
  * `m`:                        コストの減少をテストするためのパラメータ
  * `μ`:                        サブ問題の（初期）近接パラメータ
  * `ν`:                        $ν = - μ |d|^2 - c$ で与えられる停止パラメータ
  * `p::P`: 多様体 $\mathcal M$ 上の点で、現在の反復を格納
  * `p_last_serious`:           最後の真剣な反復
  * `retraction_method::AbstractRetractionMethod`: 使用する再収縮 $\operatorname{retr}$、詳細は [再収縮に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `transported_subgradients`: `p_last_serious` に輸送されるバンドルの部分勾配
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照
  * `X::T`: 多様体 $\mathcal M$ 上の点 $p$ での接ベクトルで、現在の反復での部分勾配を格納
  * `sub_problem::Union{AbstractManoptProblem, F}`: ソルバーのための問題または閉じた形の解関数を指定します。これは割り当て可能またはインプレースです。
  * `sub_state::Union{AbstractManoptProblem, F}`: 使用するサブソルバーを指定するための状態。閉じた形の解の場合、これは関数のタイプを示します。

# コンストラクタ

```
ProximalBundleMethodState(M::AbstractManifold, sub_problem, sub_state; kwargs...)
ProximalBundleMethodState(M::AbstractManifold, sub_problem=proximal_bundle_method_subsolver; evaluation=AllocatingEvaluation(), kwargs...)
```

多様体 `M` 上の [`proximal_bundle_method`](@ref) の状態を生成します。

# キーワード引数

  * `α₀=1.2`
  * `bundle_size=50`
  * `δ=1.0`
  * `ε=1e-2`
  * `μ=0.5`
  * `m=0.0125`
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収縮 $\operatorname{retr}$、詳細は [再収縮に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆再収縮 $\operatorname{retr}^{-1}$、詳細は [再収縮とその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体 $\mathcal M$ 上の点
  * `stopping_criterion=`[`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8)`[`|`](@ref StopWhenAny)[`StopAfterIteration`](@ref)`(5000)`: 停止基準が満たされていることを示すファンクタ
  * `sub_problem=`[`proximal_bundle_method_subsolver`](@ref)`: ソルバーのための問題または閉じた形の解関数を指定します。これは割り当て可能またはインプレースです。
  * `sub_state=`[`AllocatingEvaluation`](@ref): 使用するサブソルバーを指定するための状態。閉じた形の解の場合、これは関数のタイプを示します。
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)` 使用する接ベクトルのタイプを指定します。
