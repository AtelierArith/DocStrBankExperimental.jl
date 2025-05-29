```
NelderMeadState <: AbstractManoptSolverState
```

Nelder-Meadヒューリスティックに基づく最適化アルゴリズムのすべてのパラメータと状態を説明します。

# フィールド

これらのパラメータの命名は、ユークリッドの場合の[ウィキペディアの記事](https://en.wikipedia.org/wiki/Nelder–Mead_method)に従っています。デフォルトは括弧内に示され、説明の後に必要な値の範囲が示されています。

  * `population`                $n+1$点$x_i$の`Array{`point`,1}`、$i=1,…,n+1$、ここで$n$は多様体の次元です。
  * `stopping_criterion`:        ([`StopAfterIteration`](@ref)`(2000) |`[`StopWhenPopulationConcentrated`](@ref)`()`) [`StoppingCriterion`](@ref)
  * `α`:                         (`1.`) 反射パラメータ ($α > 0$)
  * `γ`:                         (`2.`) 拡張パラメータ ($γ > 0$)
  * `ρ`:                         (`1/2`) 縮小パラメータ、$0 < ρ ≤ \frac{1}{2}$、
  * `σ`:                         (`1/2`) 縮小係数、$0 < σ ≤ 1$
  * `p`:                         (`copy(population.pts[1])`) - 現在の最良値を収集するためのフィールド（ここで*いくつかの*点に初期化されます）
  * `retraction_method`:         (`default_retraction_method(M, typeof(p))`) 使用する再収縮。
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) 使用する逆再収縮。

# コンストラクタ

```
NelderMeadState(M[, population::NelderMeadSimplex]; kwargs...)
```

デフォルトの集団（提供されていない場合）として、[`NelderMeadSimplex`](@ref)に格納された`dimension(M)+1`のランダムな点のセットを持つNelder-Meadオプションを構築します。

コンストラクタでは、すべてのフィールド（集団を除く）はキーワード引数です。
