```
adaptive_regularization_with_cubics(M, f, grad_f, Hess_f, p=rand(M); kwargs...)
adaptive_regularization_with_cubics(M, f, grad_f, p=rand(M); kwargs...)
adaptive_regularization_with_cubics(M, mho, p=rand(M); kwargs...)
```

多様体 `M` 上の最適化問題を解くために、反復的に次を最小化します。

$$
  m_k(X) = f(p_k) + ⟨X, \operatorname{grad} f(p_k)⟩ + \frac{1}{2}⟨X, \operatorname{Hess} f(p_k)[X]⟩ + \frac{σ_k}{3}\lVert X \rVert^3
$$

現在の反復点 $p_k$ における接空間で、$X ∈ T_{p_k}\mathcal M$ かつ $σ_k > 0$ は正則化パラメータです。

$$
X_k
$$

をモデル $m_k$ の最小化点とし、モデル改善を使用します。

$$
  ρ_k = \frac{f(p_k) - f(\operatorname{retr}_{p_k}(X_k))}{m_k(0) - m_k(X_k) + \frac{σ_k}{3}\lVert X_k\rVert^3}.
$$

2つの閾値 $η_2 ≥ η_1 > 0$ に対して、$ρ ≥ η_1$ の場合は $p_{k+1} = \operatorname{retr}_{p_k}(X_k)$ とし、そうでない場合は候補を拒否します。すなわち、$p_{k+1} = p_k$ とします。

さらに、因子 $0 < γ_1 < 1 < γ_2$ を使用して正則化パラメータを更新します。

$$
σ_{k+1} =
\begin{cases}
    \max\{σ_{\min}, γ_1σ_k\} & \text{ if } ρ \geq η_2 &\text{   (モデルは非常に成功しました)},\\
    σ_k & \text{ if } ρ ∈ [η_1, η_2)&\text{   (モデルは成功しました)},\\
    γ_2σ_k & \text{ if } ρ < η_1&\text{   (モデルは成功しませんでした)}.
\end{cases}
$$

詳細については [AgarwalBoumalBullinsCartis:2020](@cite) を参照してください。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `f`:      最小化するコスト関数 $F: \mathcal M → ℝ$
  * `grad_f`: $F$ の勾配 $\operatorname{grad}F: \mathcal M → T \mathcal M$
  * `Hess_f`: （オプション）$F$ のヘッセ行列 $H( \mathcal M, x, ξ)$
  * `p`:      初期値 $p ∈ \mathcal M$

ヘッセ行列が提供されていない場合、ヘッセ行列は有限差分を使用して計算されます。詳細は [`ApproxHessianFiniteDifference`](@ref) を参照してください。

コスト `f` とその勾配およびヘッセ行列は、[`ManifoldHessianObjective`](@ref) として提供されることもあります。

# キーワード引数

デフォルト値は括弧内に示されています。

  * `σ`:                      (`100.0 / sqrt(manifold_dimension(M)`) 初期正則化パラメータ
  * `σmin`:                   (`1e-10`) 最小正則化値 $σ_{\min}$
  * `η1`:                     (`0.1`) モデル成功の下限閾値
  * `η2`:                     (`0.9`) モデル成功の上限閾値
  * `γ1`:                     (`0.1`) 正則化削減係数（成功の場合）
  * `γ2`:                     (`2.0`) 正則化増加係数（不成功の場合）
  * `evaluation`:             ([`AllocatingEvaluation`](@ref)) 勾配が割り当てによって動作するかどうかを指定します（デフォルト）形式 `grad_f(M, p)` または [`InplaceEvaluation`](@ref) インプレース、すなわち形式 `grad_f!(M, X, p)` およびヘッセ行列についても同様です。
  * `retraction_method`:      (`default_retraction_method(M, typeof(p))`) 使用する再収束法
  * `initial_tangent_vector`: (`zero_vector(M, p)`) 任意の接ベクトルデータを初期化します。
  * `maxIterLanczos`:         (`200`) サブソルバーの停止基準を設定するためのショートカット
  * `ρ_regularization`:       (`1e3`) コストとモデルの小さい値に対してゼロで割るのを避けるための正則化
  * `stopping_criterion`:     ([`StopAfterIteration`](@ref)`(40) |`[`StopWhenGradientNormLess`](@ref)`(1e-9) |`[`StopWhenAllLanczosVectorsUsed`](@ref)`(maxIterLanczos)`)
  * `sub_state`:              [`LanczosState`](@ref)`(M, copy(M, p); maxIterLanczos=maxIterLanczos, σ=σ)` サブ問題の状態または問題が関数である場合は [`AbstractEvaluationType`](@ref)
  * `sub_objective`:          サブ問題内で使用される目的を変更するためのショートカット
  * `sub_problem`:            [`DefaultManoptProblem`](@ref)`(M, sub_objective)` サブ問題の問題（または関数）

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的用の [`decorate_objective!`](@ref) に渡されます。直接 [`ManifoldGradientObjective`](@ref) を提供する場合でも、これらの装飾を指定できます。

デフォルトでは、`debug=` キーワードは [`DebugIfEntry`](@ref)`(:ρ_denominator, >(0); message="分母が非正です", type=:error)` に設定されており、丸め誤差によって `ρ` の計算における分母が非正になるのを避けます。
