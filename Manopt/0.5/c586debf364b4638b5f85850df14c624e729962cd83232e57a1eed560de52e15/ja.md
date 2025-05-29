```
truncated_conjugate_gradient_descent(M, f, grad_f, Hess_f, p=rand(M), X=rand(M); vector_at=p);
    kwargs...
)
truncated_conjugate_gradient_descent(M, mho::ManifoldHessianObjective, p=rand(M), X=rand(M; vector_at=p);
    kwargs...
)
truncated_conjugate_gradient_descent(M, trmo::TrustRegionModelObjective, p=rand(M), X=rand(M; vector_at=p);
    kwargs...
)
```

信頼領域の部分問題を解く

$$
\begin{align*}
\operatorname*{arg\,min}_{Y  ∈  T_p\mathcal{M}}&\ m_p(Y) = f(p) +
⟨\operatorname{grad}f(p), Y⟩_p + \frac{1}{2} ⟨\mathcal{H}_p[Y], Y⟩_p\\
\text{such that}& \ \lVert Y \rVert_p ≤ Δ
\end{align*}
$$

多様体 $\mathcal M$ 上で、Steihaug-Tointの切り捨て共役勾配法 (tCG) を使用して解決します。これは `X` の代わりに行うことができます。

アルゴリズムの説明と収束保証を提供する定理については、[AbsilBakerGallivan:2006, ConnGouldToint:2000](@cite)を参照してください。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `grad_f`: f の (リーマン) 勾配 $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ を `(M, p) -> X` または `(M, X, p) -> X` として、`X` をインプレースで計算する関数
  * `Hess_f`: f の (リーマン) ヘッセ行列 $\operatorname{Hess}f: T_{p}\mathcal M → T_{p}\mathcal M$ を `(M, p, X) -> Y` または `(M, Y, p, X) -> Y` として、`Y` をインプレースで計算する関数
  * `p`: 多様体 $\mathcal M$ 上の点
  * `X`: 多様体 $\mathcal M$ 上の点 $p$ での接ベクトル

3つの関数の代わりに、信頼領域モデルを構築するために使用される [`ManifoldHessianObjective`](@ref) `mho` を提供するか、直接 [`TrustRegionModelObjective`](@ref) `trmo` を提供します。

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref））を指定します。通常、最初の引数は多様体であり、修正された引数は2番目になります。
  * `preconditioner`:       ヘッセ行列 H の前処理器。これは、割り当て関数 `(M, p, X) -> Y` またはインプレース関数 `(M, Y, p, X) -> Y` であり、`evaluation` を参照し、デフォルトでは単位行列に設定されています。
  * `θ=1.0`:                超線形収束目標率 $1+θ$
  * `κ=0.1`:                線形収束目標率。
  * `project!=copyto!`: 数値的安定性のために、各反復後に接空間に投影することが可能です。この関数は `Y` のインプレースで動作する必要があり、すなわち `(M, Y, p, X) -> Y` であり、`X` と `Y` は同じメモリである可能性があります。
  * `randomize=false`:      `X` がランダムベクトルに初期化されるかどうかを示します。これにより前処理が無効になります。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、再tractionに関するセクションを参照してください [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(`[`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)`(base_manifold(Tpm))``)`[`|`](@ref StopWhenAny)[`StopWhenResidualIsReducedByFactorOrPower`](@ref)`(; κ=κ, θ=θ)`[`|`](@ref StopWhenAny)[`StopWhenTrustRegionIsExceeded`](@ref)`()`[`|`](@ref StopWhenAny)[`StopWhenCurvatureIsNegative`](@ref)`()`[`|`](@ref StopWhenAny)[`StopWhenModelIncreased`](@ref)`()`: 停止基準が満たされていることを示すファンクタ
  * `trust_region_radius=`[`injectivity_radius`](@extref `ManifoldsBase.injectivity_radius-Tuple{AbstractManifold}`)`(M) / 4`: 初期信頼領域半径

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、[`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードに注意してください。

# 参照

[`trust_regions`](@ref) ```
