```
truncated_conjugate_gradient_descent(M, f, grad_f, p; kwargs...)
truncated_conjugate_gradient_descent(M, f, grad_f, p, X; kwargs...)
truncated_conjugate_gradient_descent(M, f, grad_f, Hess_f; kwargs...)
truncated_conjugate_gradient_descent(M, f, grad_f, Hess_f, p; kwargs...)
truncated_conjugate_gradient_descent(M, f, grad_f, Hess_f, p, X; kwargs...)
truncated_conjugate_gradient_descent(M, mho::ManifoldHessianObjective, p, X; kwargs...)
truncated_conjugate_gradient_descent(M, trmo::TrustRegionModelObjective, p, X; kwargs...)
```

信頼領域の部分問題を解く

$$
\begin{align*}
\operatorname*{arg\,min}_{Y  ∈  T_p\mathcal{M}}&\ m_p(Y) = f(p) +
⟨\operatorname{grad}f(p), Y⟩_p + \frac{1}{2} ⟨\mathcal{H}_p[Y], Y⟩_p\\
\text{such that}& \ \lVert Y \rVert_p ≤ Δ
\end{align*}
$$

多様体 M 上で Steihaug-Toint の切り捨て共役勾配 (tCG) 法を使用して。アルゴリズムの説明と収束保証を提供する定理については、[AbsilBakerGallivan:2006, ConnGouldToint:2000](@cite)を参照してください。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `f`:      最小化するコスト関数 $f: \mathcal M → ℝ$
  * `grad_f`: `F` の勾配 $\operatorname{grad}f: \mathcal M → T\mathcal M$
  * `Hess_f`: (オプション、cf. [`ApproxHessianFiniteDifference`](@ref)) ヘッセ行列 $\operatorname{Hess}f: T_p\mathcal M → T_p\mathcal M$, $X ↦ \operatorname{Hess}F(p)[X] = ∇_X\operatorname{grad}f(p)$
  * `p`:      多様体上の点 $p ∈ \mathcal M$
  * `X`:      初期接ベクトル $X ∈ T_p\mathcal M$

3つの関数の代わりに、信頼領域モデルを構築するために使用される [`ManifoldHessianObjective`](@ref) `mho` を提供するか、直接 [`TrustRegionModelObjective`](@ref) `trmo` を提供します。

# オプション

  * `evaluation`:          ([`AllocatingEvaluation`](@ref)) 勾配とヘッセ行列が割り当てによって動作するか (デフォルト) または [`InplaceEvaluation`](@ref) でインプレースで動作するかを指定
  * `preconditioner`:      ヘッセ行列 H の前処理器
  * `θ`:                   (`1.0`) 1+θ は超線形収束目標率です。
  * `κ`:                   (`0.1`) 線形収束目標率。
  * `randomize`:           信頼領域の解決がランダムな接ベクトルで初期化される場合は true に設定します。これにより前処理が無効になります。
  * `trust_region_radius`: (`injectivity_radius(M)/4`) 信頼領域の半径
  * `project!`:            (`copyto!`) 数値的安定性のために、各反復後に接空間に投影することが可能です。デフォルトでは、これにより単にコピーされます。
  * `stopping_criterion`:  ([`StopAfterIteration`](@ref)`(manifol_dimension(M)) |`[`StopWhenResidualIsReducedByFactorOrPower`](@ref)`(;κ=κ, θ=θ) |`[`StopWhenCurvatureIsNegative`](@ref)`() |`[`StopWhenTrustRegionIsExceeded`](@ref)`() |`[`StopWhenModelIncreased`](@ref)`()`) [`StoppingCriterion`](@ref) から継承されたファンクタで、いつ停止するかを示します。

および、デコレーター用に [`decorate_state!`](@ref) に渡されるもの。

# 出力

得られた (近似的な) 最小化点 $Y^*$、詳細については [`get_solver_return`](@ref) を参照してください。

# 参照

[`trust_regions`](@ref)
