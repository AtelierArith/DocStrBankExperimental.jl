```
subgradient_method(M, f, ∂f, p=rand(M); kwargs...)
subgradient_method(M, sgo, p=rand(M); kwargs...)
```

サブグラディエント法を実行します $p_{k+1} = \mathrm{retr}(p_k, s_k∂f(p_k))$、

ここで $\mathrm{retr}$ はリトラクション、$s_k$ はステップサイズで、通常は [`ConstantStepsize`](@ref) ですが、指定することもできます。サブグラディエントは値集合を持つ可能性がありますが、引数 `∂f` は常にサブ微分から *1* つの要素を返すべきですが、必ずしも決定論的ではありません。詳細については [FerreiraOliveira:1998](@cite) を参照してください。

# 入力

  * `M`:  マニフォールド $\mathcal M$
  * `f`:  最小化するコスト関数 $f:\mathcal M→ℝ$
  * `∂f`: (サブ)グラディエント $∂ f: \mathcal M→ T\mathcal M$ で、常にサブ微分から1つの値/要素のみを返すように制限されています。この関数は、割り当て関数 `(M, p) -> X` または変異関数 `(M, X, p) -> X` として渡すことができ、`evaluation` を参照してください。
  * `p`:  （`rand(M)`）初期値 $p_0=p ∈ \mathcal M$

`f` と `∂f` の代わりに [`ManifoldSubgradientObjective`](@ref) `sgo` を提供することもできます。

# オプション

  * `evaluation`:         （[`AllocatingEvaluation`](@ref)）サブグラディエントが割り当てによって動作するかどうかを指定します（デフォルト）形式 `∂f(M, y)` または [`InplaceEvaluation`](@ref) 形式 `∂f!(M, X, x)` の代わりに。
  * `retraction`:         （`default_retraction_method(M, typeof(p))`）使用するリトラクション。
  * `stepsize`:           （[`ConstantStepsize`](@ref)`(M)`）[`Stepsize`](@ref) を指定します。
  * `stopping_criterion`: （[`StopAfterIteration`](@ref)`(5000)`）ファンクタ、[`StoppingCriterion`](@ref) を参照し、いつ停止するかを示します。

および [`decorate_state!`](@ref) に渡されるデコレーター用のもの。

# 出力

得られた（近似的な）最小化点 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください。
