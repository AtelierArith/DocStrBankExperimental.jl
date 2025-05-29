```
gradient_descent(M, f, grad_f, p=rand(M); kwargs...)
gradient_descent(M, gradient_objective, p=rand(M); kwargs...)
```

勾配降下法を実行します

$$
p_{k+1} = \operatorname{retr}_{p_k}\bigl( s_k\operatorname{grad}f(p_k) \bigr),
\qquad k=0,1,…
$$

異なるステップサイズ $s_k$ の選択肢が利用可能です（以下の `stepsize` オプションを参照）。

# 入力

  * `M`       マンフォールド $\mathcal M$
  * `f`       最小化子 $p^*$ を見つけるためのコスト関数 $f: \mathcal M→ℝ$
  * `grad_f`  関数 `(M, p) -> X` または `(M, X, p) -> X` としての f の勾配 $\operatorname{grad}f: \mathcal M → T\mathcal M$
  * `p`       初期値 `p` $= p_0 ∈ \mathcal M$

`f` と `grad_f` の代わりに、[`AbstractManifoldGradientObjective`](@ref) `gradient_objective` を直接提供することができます。

# オプション

  * `direction`:          ([`IdentityUpdateRule`](@ref)) 方向の処理を実行します。例：
  * `evaluation`:         ([`AllocatingEvaluation`](@ref)) 勾配が割り当てによって動作するか（デフォルト）`grad_f(M, p)` の形式、または [`InplaceEvaluation`](@ref) の形式 `grad_f!(M, X, p)` であるかを指定します。
  * `retraction_method`:  ([`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`) 使用する再traction
  * `stepsize`:           ([`default_stepsize`](@ref)`(M, GradientDescentState)`) [`Stepsize`](@ref)
  * `stopping_criterion`: ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenGradientNormLess`](@ref)`(1e-8)`) 停止するタイミングを示す [`StoppingCriterion`](@ref) から継承されたファンクタ。
  * `X`:                  ([`zero_vector(M,p)`]) 使用する勾配のメモリおよび/または型を提供します。

[`ManifoldGradientObjective`](@ref) を直接提供する場合、`evaluation` は無視されます。

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的用の [`decorate_objective!`](@ref) に渡されます。[`ManifoldGradientObjective`](@ref) を直接提供する場合、これらの装飾も指定できます。

# 出力

得られた（近似的な）最小化子 $p^*$。ソルバーの最終状態全体を取得するには、詳細については [`get_solver_return`](@ref) を参照してください。
