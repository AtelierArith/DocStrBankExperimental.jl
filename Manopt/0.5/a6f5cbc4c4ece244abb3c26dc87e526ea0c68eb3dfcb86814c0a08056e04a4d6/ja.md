```
NelderMeadState <: AbstractManoptSolverState
```

Nelder-Meadヒューリスティックに基づく最適化アルゴリズムのすべてのパラメータと状態を説明します。

# フィールド

これらのパラメータの命名は、ユークリッドの場合の[ウィキペディアの記事](https://en.wikipedia.org/wiki/Nelder–Mead_method)に従っています。デフォルトは括弧内に示され、説明の後に必要な値の範囲が示されています。

  * `population::`[`NelderMeadSimplex`](@ref): $d+1$点 $x_i$ の集まり（セット）、$i=1,…,n+1$、ここで $d$ は `M` の[`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)です。
  * `stepsize::Stepsize`: ステップサイズを決定するための[`Stepsize`](@ref)から継承されたファンクタ
  * `α`: 反射パラメータ $α > 0$:
  * `γ`: 拡張パラメータ $γ > 0$:
  * `ρ`: 縮小パラメータ、$0 < ρ ≤ \frac{1}{2}$,
  * `σ`: 縮小係数、$0 < σ ≤ 1$
  * `p::P`: 現在の最良点を格納する多様体 $\mathcal M$ 上の点
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `retraction_method::AbstractRetractionMethod`: 使用する引き戻し $\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照

# コンストラクタ

```
NelderMeadState(M::AbstractManifold; kwargs...)
```

デフォルトの集団（提供されていない場合）を持つNelder-Meadオプションを構築し、[`NelderMeadSimplex`](@ref)に格納された`dimension(M)+1`のランダムな点のセットを持ちます。

# キーワード引数

  * `population=`[`NelderMeadSimplex`](@ref)`(M)`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(2000)`[`|`](@ref StopWhenAny)[`StopWhenPopulationConcentrated`](@ref)`()`：停止基準が満たされていることを示すファンクタ、[`StoppingCriterion`](@ref)
  * `α=1.0`: 反射パラメータ $α > 0$:
  * `γ=2.0` 拡張パラメータ $γ$:
  * `ρ=1/2`: 縮小パラメータ、$0 < ρ ≤ \frac{1}{2}$,
  * `σ=1/2`: 縮小係数、$0 < σ ≤ 1$
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `p=copy(M, population.pts[1])`: 最良点（反復）のストレージを初期化する
