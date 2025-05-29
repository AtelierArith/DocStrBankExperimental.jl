```
adaptive_regularization_with_cubics(M, f, grad_f, Hess_f, p=rand(M); kwargs...)
adaptive_regularization_with_cubics(M, f, grad_f, p=rand(M); kwargs...)
adaptive_regularization_with_cubics(M, mho, p=rand(M); kwargs...)
adaptive_regularization_with_cubics!(M, f, grad_f, Hess_f, p; kwargs...)
adaptive_regularization_with_cubics!(M, f, grad_f, p; kwargs...)
adaptive_regularization_with_cubics!(M, mho, p; kwargs...)
```

マンフォールド `M` 上の最適化問題を解決するために、次のように反復的に最小化します。

$$
m_k(X) = f(p_k) + ⟨X, \operatorname{grad} f(p^{(k)})⟩ + \frac{1}{2}⟨X, \operatorname{Hess} f(p^{(k)})[X]⟩ + \frac{σ_k}{3}\lVert X \rVert^3
$$

現在の反復点 $p_k$ における接空間で、$X ∈ T_{p_k}\mathcal M$ であり、$σ_k > 0$ は正則化パラメータです。

$$
Xp^{(k)}
$$

をモデル $m_k$ の最小化点とし、モデル改善を使用します。

$$
  ρ_k = \frac{f(p_k) - f(\operatorname{retr}_{p_k}(X_k))}{m_k(0) - m_k(X_k) + \frac{σ_k}{3}\lVert X_k\rVert^3}.
$$

2つの閾値 $η_2 ≥ η_1 > 0$ を用いて、$ρ ≥ η_1$ の場合は $p_{k+1} = \operatorname{retr}_{p_k}(X_k)$ とし、そうでない場合は候補を拒否します。つまり、$p_{k+1} = p_k$ とします。

さらに、正則化パラメータを次のように更新します。

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

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `grad_f`: 関数 `(M, p) -> X` または `(M, X, p) -> X` として、$f$ の (リーマン) 勾配 $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$
  * `Hess_f`: 関数 `(M, p, X) -> Y` または `(M, Y, p, X) -> Y` として、$f$ の (リーマン) ヘッセ行列 $\operatorname{Hess}f: T_{p}\mathcal M → T_{p}\mathcal M$
  * `p`: 多様体 $\mathcal M$ 上の点

コスト `f` とその勾配およびヘッセ行列は、[`ManifoldHessianObjective`](@ref) としても提供される場合があります。

# キーワード引数

  * `σ=100.0 / sqrt(manifold_dimension(M)`: 初期正則化パラメータ
  * `σmin=1e-10`: 最小正則化値 $σ_{\min}$
  * `η1=0.1`: 下限モデル成功閾値
  * `η2=0.9`: 上限モデル成功閾値
  * `γ1=0.1`: 正則化削減係数（成功の場合）
  * `γ2=2.0`: 正則化増加係数（不成功の場合）
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが結果を割り当てて返すか、入力引数を修正して結果を返すかを指定します（[`AllocatingEvaluation`](@ref) または [`InplaceEvaluation`](@ref)）。通常、最初の引数は多様体であり、修正された引数は2番目になります。
  * `initial_tangent_vector=zero_vector(M, p)`: 任意の接ベクトルデータを初期化します。
  * `maxIterLanczos=200`: サブソルバーの停止基準を設定するためのショートカット。
  * `ρ_regularization=1e3`: コストとモデルの小さい値でゼロ除算を避けるための正則化。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、再tractionに関するセクションを参照してください。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(40)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-9)`[`|`](@ref StopWhenAny)[`StopWhenAllLanczosVectorsUsed`](@ref)`(maxIterLanczos)`: 停止基準が満たされていることを示すファンクタ。
  * `sub_kwargs=``(;)`: サブソルバーの目的の [`decorate_objective!`](@ref)、サブソルバーの状態の [`decorate_state!`](@ref)、およびサブ状態コンストラクタ自体に渡されるキーワード引数の名前付きタプル。
  * `sub_objective=nothing`: `sub_problem=` キーワード内で使用されるサブ問題の目的を変更するためのショートカット。デフォルトでは、これは [`AdaptiveRagularizationWithCubicsModelObjective`](@ref) として初期化され、`sub_kwargs=` キーワードを使用してさらに装飾できます。
  * `sub_state=`[`LanczosState`](@ref)`(M, copy(M,p))`: 使用するサブソルバーを指定する状態。閉じた形式の解決策の場合、これは関数のタイプを示します。
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`: ソルバーまたは閉じた形式の解決策関数の問題を指定します。これは割り当て可能またはインプレースである可能性があります。

他のすべてのキーワード引数は、状態デコレーターのための [`decorate_state!`](@ref) または目的デコレーターのための [`decorate_objective!`](@ref) に渡されます。

[`ManifoldGradientObjective`](@ref) を直接提供する場合、`evaluation=` キーワードは無視されます。装飾は目的に対して適用されます。

チュートリアルモードを有効にすると（cf. [`is_tutorial_mode`](@ref)）、このソルバーは追加のデバッグ警告を提供します。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、特に `return_state=` キーワードの詳細については [`get_solver_return`](@ref) を参照してください。
