```
exact_penalty_method(M, f, grad_f, p=rand(M); kwargs...)
exact_penalty_method(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
exact_penalty_method!(M, f, grad_f, p; kwargs...)
exact_penalty_method!(M, cmo::ConstrainedManifoldObjective, p; kwargs...)
```

正確ペナルティ法 (EPM) [LiuBoumal:2019](@cite) の実行。EPMの目的は、制約付き最適化タスクの解を見つけることです。

$$
\begin{aligned}
\operatorname*{arg\,min}_{p ∈ \mathcal M} & f(p)\\
\text{subject to}\quad&g_i(p) ≤ 0 \quad \text{ for } i= 1, …, m,\\
\quad & h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

ここで `M` はリーマン多様体であり、$f$、$\{g_i\}_{i=1}^{n}$ および $\{h_j\}_{j=1}^{m}$ は `M` から ℝ への2回連続微分可能な関数です。そのため、目的関数に制約違反のための重み付き $L_1$ ペナルティ項が追加されます。

$$
f(x) + ρ\biggl( \sum_{i=1}^m \max\bigl\{0, g_i(x)\bigr\} + \sum_{j=1}^n \vert h_j(x)\vert\biggr),
$$

ここで $ρ>0$ はペナルティパラメータです。

これは非滑らかであるため、[`SmoothingTechnique`](@ref) がパラメータ `u` で適用されます。詳細は [`ExactPenaltyCost`](@ref) を参照してください。

正確ペナルティ法の各ステップ $k$ では、滑らかにした目的関数がすべての $p ∈\mathcal M$ に対して最小化されます。その後、精度許容値 $ϵ$ と滑らかさパラメータ $u$ は次のように更新されます。

$$
ϵ^{(k)}=\max\{ϵ_{\min}, θ_ϵ ϵ^{(k-1)}\},
$$

ここで $ϵ_{\min}$ は $ϵ$ が許可される最小値であり、$θ_ϵ ∈ (0,1)$ は定数スケーリング因子です。また、

$$
u^{(k)} = \max \{u_{\min}, \theta_u u^{(k-1)} \},
$$

ここで $u_{\min}$ は $u$ が許可される最小値であり、$θ_u ∈ (0,1)$ は定数スケーリング因子です。

最後に、ペナルティパラメータ $ρ$ は次のように更新されます。

$$
ρ^{(k)} = \begin{cases}
ρ^{(k-1)}/θ_ρ,  & \text{if } \displaystyle \max_{j ∈ \mathcal{E},i ∈ \mathcal{I}} \Bigl\{ \vert h_j(x^{(k)}) \vert, g_i(x^{(k)})\Bigr\} \geq u^{(k-1)} \Bigr) ,\\
ρ^{(k-1)}, & \text{else,}
\end{cases}
$$

ここで $θ_ρ ∈ (0,1)$ は定数スケーリング因子です。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `grad_f`: 関数 `(M, p) -> X` または関数 `(M, X, p) -> X` として、$f$ の (リーマン) 勾配 $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ を計算する
  * `p`: 多様体 $\mathcal M$ 上の点

# キーワード引数

[`ConstrainedManifoldObjective`](@ref) `cmo` で呼び出されない場合

  * `g=nothing`: 不等式制約
  * `h=nothing`: 等式制約
  * `grad_g=nothing`: 不等式制約の勾配
  * `grad_h=nothing`: 等式制約の勾配

(`g`, `grad_g`) または (`h`, `grad_h`) のいずれかのペアを提供する必要があります。そうでない場合、問題は制約されておらず、より良いソルバーは例えば [`quasi_Newton`](@ref) です。

# その他のキーワード引数

  * `ϵ=1e–3`: 精度許容値
  * `ϵ_exponent=1/100`: ϵ 更新因子の指数;
  * `ϵ_min=1e-6`: 精度許容値の下限
  * `u=1e–1`: 滑らかさパラメータおよび制約違反の閾値
  * `u_exponent=1/100`: u 更新因子の指数;
  * `u_min=1e-6`: 滑らかさパラメータおよび制約違反の閾値の下限
  * `ρ=1.0`: ペナルティパラメータ
  * `equality_constraints=nothing`: 等式制約の数 $n$。提供されない場合、$g$ の勾配を呼び出してこれを推定します。
  * `gradient_range=nothing`: 制約の両方の勾配がどのように表現されるかを指定
  * `gradient_equality_range=gradient_range`: 等式制約の勾配がどのように表現されるかを指定、[`VectorGradientFunction`](@ref) を参照。
  * `gradient_inequality_range=gradient_range`: 不等式制約の勾配がどのように表現されるかを指定、[`VectorGradientFunction`](@ref) を参照。
  * `inequality_constraints=nothing`: 不等式制約の数 $m$。提供されない場合、$g$ の勾配を呼び出してこれを推定します。
  * `min_stepsize=1e-10`: 最小ステップサイズ
  * `smoothing=`[`LogarithmicSumOfExponentials`](@ref): 使用する [`SmoothingTechnique`](@ref)
  * `sub_cost=`[`ExactPenaltyCost`](@ref)`(problem, ρ, u; smoothing=smoothing)`: サブソルバーで使用するコスト。これは `sub_problem=` キーワードを定義するために使用され、直接 `sub_problem` を設定した場合は効果がありません。
  * `sub_grad=`[`ExactPenaltyGrad`](@ref)`(problem, ρ, u; smoothing=smoothing)`: サブソルバーで使用する勾配。これは `sub_problem=` キーワードを定義するために使用され、直接 `sub_problem` を設定した場合は効果がありません。
  * `sub_kwargs=``(;)`: サブソルバーの目的の [`decorate_objective!`](@ref)、サブソルバーの状態の [`decorate_state!`](@ref)、およびサブ状態コンストラクタ自体に渡されるキーワード引数の名前付きタプル。
  * `sub_stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(ϵ)`[`|`](@ref StopWhenAny)[`StopWhenStepsizeLess`](@ref)`(1e-10)`: サブソルバーの停止基準。これは `sub_state=` キーワードを定義するために使用され、直接 `sub_state` を設定した場合は効果がありません。
  * `sub_state=`[`DefaultManoptProblem`](@ref)`(M,`[`ManifoldGradientObjective`](@ref)`(sub*cost, sub*grad; evaluation=evaluation): 使用するサブソルバーを指定する状態。閉じた形式の解の場合、これは関数のタイプを示します。
  * `sub_state=`[`QuasiNewtonState`](@ref): 使用するサブソルバーを指定する状態。閉じた形式の解の場合、これは関数のタイプを示します。ここで [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) と [`InverseBFGS`](@ref) が使用されます。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)`(`[`StopWhenSmallerOrEqual`](@ref)`(ϵ, ϵ_min)`[`&`](@ref StopWhenAll)[`StopWhenChangeLess`](@ref)`(1e-10) )`: 停止基準が満たされていることを示すファンクタ。

制約の勾配の `range` に関しては、他のパワー多様体接線空間表現、主に [`ArrayPowerRepresentation`](@extref Manifolds :jl:type:`Manifolds.ArrayPowerRepresentation`) が使用される場合があります。勾配がその表現でより効率的に計算できる場合です。

他のすべてのキーワード引数は、状態デコレーターのために [`decorate_state!`](@ref) に渡されるか、目的デコレーターのために [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの最終状態全体を取得するには、詳細については [`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードを参照してください。
