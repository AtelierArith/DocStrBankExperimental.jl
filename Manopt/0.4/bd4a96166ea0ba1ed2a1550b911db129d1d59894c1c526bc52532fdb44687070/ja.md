```
exact_penalty_method(M, F, gradF, p=rand(M); kwargs...)
exact_penalty_method(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
```

正確ペナルティ法 (EPM) [LiuBoumal:2019](@cite) を実行します。EPMの目的は、制約付き最適化タスクの解を見つけることです。

$$
\begin{aligned}
\min_{p ∈\mathcal{M}} &f(p)\\
\text{subject to } &g_i(p)\leq 0 \quad \text{ for } i= 1, …, m,\\
\quad &h_j(p)=0 \quad  \text{ for } j=1,…,n,
\end{aligned}
$$

ここで `M` はリーマン多様体であり、$f$、$\{g_i\}_{i=1}^m$ および $\{h_j\}_{j=1}^n$ は `M` から ℝ への二回連続微分可能な関数です。そのため、目的関数に制約違反のための重み付き $L_1$ ペナルティ項が追加されます。

$$
f(x) + ρ\biggl( \sum_{i=1}^m \max\bigl\{0, g_i(x)\bigr\} + \sum_{j=1}^n \vert h_j(x)\vert\biggr),
$$

ここで $ρ>0$ はペナルティパラメータです。これは非滑らかであるため、[`SmoothingTechnique`](@ref) がパラメータ `u` で適用されます。詳細は [`ExactPenaltyCost`](@ref) を参照してください。

正確ペナルティ法の各ステップ $k$ では、滑らかにした目的関数がすべての $x ∈\mathcal{M}$ に対して最小化されます。その後、精度許容値 $ϵ$ と滑らかさパラメータ $u$ は次のように設定して更新されます。

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

  * `M`      多様体 $\mathcal M$
  * `f`      最小化するコスト関数 $f:\mathcal M→ℝ$
  * `grad_f` コスト関数の勾配

# オプション（[`ConstrainedManifoldObjective`](@ref) `cmo` で呼び出されない場合）

  * `g`:      （`nothing`）不等式制約
  * `h`:      （`nothing`）等式制約
  * `grad_g`: （`nothing`）不等式制約の勾配
  * `grad_h`: （`nothing`）等式制約の勾配

`(g, grad_g)` または `(h, grad_h)` のいずれかのペアを提供する必要があります。そうでない場合、問題は制約されておらず、[`quasi_Newton`](@ref) のような無制約ソルバーの使用を検討する必要があります。

# オプション

  * `smoothing`:                 ([`LogarithmicSumOfExponentials`](@ref)) 使用する [`SmoothingTechnique`](@ref)
  * `ϵ`:                         （`1e–3`）精度許容値
  * `ϵ_exponent`:                （`1/100`）ϵ 更新因子の指数；
  * `ϵ_min`:                     （`1e-6`）精度許容値の下限
  * `u`:                         （`1e–1`）滑らかさパラメータおよび制約違反の閾値
  * `u_exponent`:                （`1/100`）u 更新因子の指数；
  * `u_min`:                     （`1e-6`）滑らかさパラメータおよび制約違反の閾値の下限
  * `ρ`:                         （`1.0`）ペナルティパラメータ
  * `equality_constraints`:      （`nothing`）等式制約の数 $n$。
  * `gradient_range`             （`nothing`、[`NestedPowerRepresentation`](@extref) と同等）勾配がどのように表現されるかを指定
  * `gradient_equality_range`:   （`gradient_range`）等式制約の勾配がどのように表現されるかを指定
  * `gradient_inequality_range`: （`gradient_range`）不等式制約の勾配がどのように表現されるかを指定
  * `inequality_constraints`:    （`nothing`）不等式制約の数 $m$。
  * `min_stepsize`:              （`1e-10`）最小ステップサイズ
  * `sub_cost`:                  ([`ExactPenaltyCost`](@ref)`(problem, ρ, u; smoothing=smoothing)`) この正確ペナルティコストを使用、特にサブ問題のオプションと同じ数 `ρ,u` を使用
  * `sub_grad`:                  ([`ExactPenaltyGrad`](@ref)`(problem, ρ, u; smoothing=smoothing)`) この正確ペナルティ勾配を使用、特にサブ問題のオプションと同じ数 `ρ,u` を使用
  * `sub_kwargs`:                （`(;)`）サブオプションを装飾するためのキーワード引数、デバッグなど、メインソルバーのデバッグオプション（サブサンプリングなど）を自動的に尊重します。
  * `sub_stopping_criterion`:    ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenGradientNormLess`](@ref)`(ϵ) |`[`StopWhenStepsizeLess`](@ref)`(1e-10)`) サブソルバーの停止基準を指定。
  * `sub_problem`:               ([`DefaultManoptProblem`](@ref)`(M,`[`ManifoldGradientObjective`](@ref)`(sub_cost, sub_grad; evaluation=evaluation)`, サブソルバーのための問題を提供
  * `sub_state`:                 ([`QuasiNewtonState`](@ref)) [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) を使用し、[`InverseBFGS`](@ref) と `sub_stopping_criterion` を停止基準として使用。`sub_kwargs` も参照してください。
  * `stopping_criterion`:        ([`StopAfterIteration`](@ref)`(300)` | ([`StopWhenSmallerOrEqual`](@ref)`(ϵ, ϵ_min)` & [`StopWhenChangeLess`](@ref)`(1e-10)`) [`StoppingCriterion`](@ref) から継承されたファンクタで、停止するタイミングを示します。

制約の勾配の `range` については、他のパワーマンフォールド接線空間表現、主に [`ArrayPowerRepresentation`](@extref Manifolds :jl:type:`Manifolds.ArrayPowerRepresentation`) を使用することができます。勾配がその表現でより効率的に計算できる場合です。

`equality_constraints` と `inequality_constraints` では、それぞれ `h` と `g` の範囲の次元を提供する必要があります。提供されない場合、`M` と開始点 `p0` とともに、これらのいずれかを呼び出して推測を試みます。

# 出力

得られた（近似的な）最小化点 $p^*$、詳細は [`get_solver_return`](@ref) を参照してください。
