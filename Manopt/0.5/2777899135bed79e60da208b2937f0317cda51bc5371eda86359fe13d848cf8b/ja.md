```
ChambollePockState <: AbstractPrimalDualSolverState
```

は、線形化されたまたは正確なChambolle Pock内のすべてのオプションと変数を格納します。

# フィールド

  * `acceleration::R`:    加速因子
  * `dual_stepsize::R`:   双対近接の近接パラメータ
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `inverse_retraction_method_dual::AbstractInverseRetractionMethod`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `m::P`:               $\mathcal M$上の基準点
  * `n::Q`:               $\mathcal N$上の基準点
  * `p::P`:               $p^{(0)} ∈ \mathcal M$上の初期点
  * `pbar::P`:            次の双対更新ステップで使用される緩和反復（`:primal`緩和を使用する場合）
  * `primal_stepsize::R`: 主近接の近接パラメータ
  * `X::T`:               初期接ベクトル $X^{(0)} ∈ T_{p^{(0)}}\mathcal M$
  * `Xbar::T`:            次の主更新ステップで使用される緩和反復（`:dual`緩和を使用する場合）
  * `relaxation::R`:      主緩和ステップでの緩和（`pbar`を計算するため）
  * `relax::Symbol:       どの変数を緩和するか（`:primal`または`:dual`）
  * `retraction_method::AbstractRetractionMethod`: 使用する引き戻し $\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `variant`:            `:exact`または`:linearized`のChambolle-Pockを実行するかどうか
  * `update_primal_base`: 関数 `(pr, st, k) -> m` 主基準を更新するため
  * `update_dual_base`:  関数 `(pr, st, k) -> n` 双対基準を更新するため
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照
  * `vector_transport_method_dual::AbstractVectorTransportMethodP`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照

ここで、`P`は$\mathcal M$上の点の型、`T`はその接ベクトル型、`Q`は$\mathcal N$上の点の型、`R<:Real`は実数型です。

最後の2つの関数では、[`AbstractManoptProblem`](@ref)`p`、[`AbstractManoptSolverState`](@ref)`o`、および現在の反復`i`が引数です。これらをデフォルトの恒等式と異なるように有効にする場合、アルゴリズムが機能するために`p.Λ`を提供する必要があります（線形化された場合は`missing`である可能性があります）。

# コンストラクタ

```
ChambollePockState(M::AbstractManifold, N::AbstractManifold;
    kwargs...
) where {P, Q, T, R <: Real}
```

# キーワード引数

  * `n=``[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(N)`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`
  * `m=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`
  * `acceleration=0.0`
  * `dual_stepsize=1/sqrt(8)`
  * `primal_stepsize=1/sqrt(8)`
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `inverse_retraction_method_dual=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(N, typeof(n))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `relaxation=1.0`
  * `relax=:primal`: デフォルトで主変数を緩和
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`: 停止基準が満たされていることを示すファンクタ
  * `variant=:exact`: デフォルトで正確なChambolle Pockを実行
  * `update_primal_base=missing`
  * `update_dual_base=missing`
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照
  * `vector_transport_method_dual=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(N, typeof(n))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照

`Manifolds.jl`がロードされている場合、`N`もキーワード引数であり、デフォルトで`TangentBundle(M)`に設定されます。
