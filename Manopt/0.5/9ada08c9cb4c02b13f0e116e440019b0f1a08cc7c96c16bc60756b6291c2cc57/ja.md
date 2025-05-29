```
subgradient_method(M, f, ∂f, p=rand(M); kwargs...)
subgradient_method(M, sgo, p=rand(M); kwargs...)
subgradient_method!(M, f, ∂f, p; kwargs...)
subgradient_method!(M, sgo, p; kwargs...)
```

サブグラディエント法を実行します $p^{(k+1)} = \operatorname{retr}\bigl(p^{(k)}, s^{(k)}∂f(p^{(k)})\bigr)$、ここで $\operatorname{retr}$ はリトラクション、$s^{(k)}$ はステップサイズです。

サブグラディエントは値集合である可能性がありますが、引数 `∂f` は常にサブグラディエントからの*1つの*要素を返すべきですが、必ずしも決定論的ではありません。詳細については [FerreiraOliveira:1998](@cite) を参照してください。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ は `(M, p) -> v` として実装されています
  * `∂f`: f の (サブ)グラディエント $∂ f: \mathcal M → T\mathcal M$
  * `p`: 多様体 $\mathcal M$ 上の点

`f` と `∂f` の代わりに [`ManifoldSubgradientObjective`](@ref) `sgo` を提供することができます。

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることによって動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目のものです。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するリトラクション $\operatorname{retr}$、リトラクションに関するセクションを参照してください [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`default_stepsize`](@ref)`(M, SubGradientMethodState)`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(5000)`: 停止基準が満たされていることを示すファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ での接ベクトルを指定して接ベクトルの表現を指定します

および [`decorate_state!`](@ref) に渡されるデコレーター用の引数。

# 出力

得られた (近似的な) 最小化点 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください ```
