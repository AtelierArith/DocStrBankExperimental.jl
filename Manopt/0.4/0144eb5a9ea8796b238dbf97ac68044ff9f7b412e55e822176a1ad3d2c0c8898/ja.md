```
augmented_Lagrangian_method(M, f, grad_f, p=rand(M); kwargs...)
augmented_Lagrangian_method(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
```

拡張ラグランジュ法 (ALM) [LiuBoumal:2019](@cite) を実行します。

ALMの目的は、制約付き最適化タスクの解を見つけることです。

$$
\begin{aligned}
\min_{p ∈\mathcal{M}} &f(p)\\
\text{subject to } &g_i(p)\leq 0 \quad \text{ for } i= 1, …, m,\\
\quad &h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

ここで `M` はリーマン多様体であり、$f$、$\{g_i\}_{i=1}^m$ および $\{h_j\}_{j=1}^p$ は `M` から ℝ への2回連続微分可能な関数です。アルゴリズムの各ステップ $k$ では、[`AugmentedLagrangianCost`](@ref) $\mathcal{L}_{ρ^{(k-1)}}(p, μ^{(k-1)}, λ^{(k-1)})$ が $\mathcal{M}$ 上で最小化されます。ここで、$μ^{(k-1)} ∈ \mathbb R^n$ および $λ^{(k-1)} ∈ ℝ^m$ はラグランジュ乗数の現在の反復値であり、$ρ^{(k-1)}$ は現在のペナルティパラメータです。

次に、ラグランジュ乗数は次のように更新されます。

$$
λ_j^{(k)} =\operatorname{clip}_{[λ_{\min},λ_{\max}]} (λ_j^{(k-1)} + ρ^{(k-1)} h_j(p^{(k)})) \text{for all} j=1,…,p,
$$

および

$$
μ_i^{(k)} =\operatorname{clip}_{[0,μ_{\max}]} (μ_i^{(k-1)} + ρ^{(k-1)} g_i(p^{(k)})) \text{ for all } i=1,…,m,
$$

ここで $λ_{\min} \leq λ_{\max}$ および $μ_{\max}$ は乗数の境界です。

次に、精度許容値 $ϵ$ は次のように更新されます。

$$
ϵ^{(k)}=\max\{ϵ_{\min}, θ_ϵ ϵ^{(k-1)}\},
$$

ここで $ϵ_{\min}$ は $ϵ$ が許可される最小値であり、$θ_ϵ ∈ (0,1)$ は定数スケーリングファクターです。

最後に、ペナルティパラメータ $ρ$ は次のように更新されます。

$$
σ^{(k)}=\max_{j=1,…,p, i=1,…,m} \{\|h_j(p^{(k)})\|, \|\max_{i=1,…,m}\{g_i(p^{(k)}), -\frac{μ_i^{(k-1)}}{ρ^{(k-1)}} \}\| \}.
$$

`ρ` は次のように更新されます。

$$
ρ^{(k)} = \begin{cases}
ρ^{(k-1)}/θ_ρ,  & \text{if } σ^{(k)}\leq θ_ρ σ^{(k-1)} ,\\
ρ^{(k-1)}, & \text{else,}
\end{cases}
$$

ここで $θ_ρ ∈ (0,1)$ は定数スケーリングファクターです。

# 入力

  * `M`      多様体 $\mathcal M$
  * `f`      最小化するコスト関数 $F:\mathcal M→ℝ$
  * `grad_f` コスト関数の勾配

# オプション ([`ConstrainedManifoldObjective`](@ref) `cmo` で呼び出されない場合)

  * `g`:      (`nothing`) 不等式制約
  * `h`:      (`nothing`) 等式制約
  * `grad_g`: (`nothing`) 不等式制約の勾配
  * `grad_h`: (`nothing`) 等式制約の勾配

`(g, grad_g)` または `(h, grad_h)` のいずれかのペアを提供する必要があります。そうでない場合、問題は制約されておらず、より良いソルバーは例えば [`quasi_Newton`](@ref) です。

# オプション

  * `ϵ`:                         (`1e-3`) 精度許容値
  * `ϵ_min`:                     (`1e-6`) 精度許容値の下限
  * `ϵ_exponent`:                (`1/100`) ϵ 更新ファクターの指数; また、アルゴリズムが自然に終了するまでの最大精度が必要な反復回数の逆数
  * `θ_ϵ`:                       (`(ϵ_min / ϵ)^(ϵ_exponent)`) 正確さのスケーリングファクター
  * `μ`:                         (`ones(size(h(M,x),1))`) 不等式制約に関するラグランジュ乗数
  * `μ_max`:                     (`20.0`) 不等式制約に属するラグランジュ乗数の上限
  * `λ`:                         (`ones(size(h(M,x),1))`) 等式制約に関するラグランジュ乗数
  * `λ_max`:                     (`20.0`) 等式制約に属するラグランジュ乗数の上限
  * `λ_min`:                     (`- λ_max`) 等式制約に属するラグランジュ乗数の下限
  * `τ`:                         (`0.8`) ペナルティパラメータの評価改善のためのファクター
  * `ρ`:                         (`1.0`) ペナルティパラメータ
  * `θ_ρ`:                       (`0.3`) ペナルティパラメータのスケーリングファクター
  * `equality_constraints`:      (`nothing`) 等式制約の数 $n$。
  * `gradient_range`             (`nothing`, equivalent to [`NestedPowerRepresentation`](@extref) 勾配がどのように表現されるかを指定
  * `gradient_equality_range`:   (`gradient_range`) 等式制約の勾配がどのように表現されるかを指定
  * `gradient_inequality_range`: (`gradient_range`) 不等式制約の勾配がどのように表現されるかを指定
  * `inequality_constraints`:    (`nothing`) 不等式制約の数 $m$。
  * `sub_grad`:                  ([`AugmentedLagrangianGrad`](@ref)`(problem, ρ, μ, λ)`) 拡張ラグランジュ勾配を使用し、特にサブ問題のオプションと同じ数 `ρ,μ` を使用
  * `sub_kwargs`:                (`(;)`) サブオプションを装飾するためのキーワード引数、例えば `debug=` キーワード。
  * `sub_stopping_criterion`:    ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenGradientNormLess`](@ref)`(ϵ) |`[`StopWhenStepsizeLess`](@ref)`(1e-8)`) サブソルバーの停止基準を指定。
  * `sub_problem`:               ([`DefaultManoptProblem`](@ref)`(M,`[`ConstrainedManifoldObjective`](@ref)`(subcost, subgrad; evaluation=evaluation))`) サブソルバーの問題
  * `sub_state`:                 ([`QuasiNewtonState`](@ref)) [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) を使用し、[`InverseBFGS`](@ref) と `sub_stopping_criterion` を停止基準として使用。`sub_kwargs` も参照。
  * `stopping_criterion`:        ([`StopAfterIteration`](@ref)`(300)` | ([`StopWhenSmallerOrEqual`](@ref)`(ϵ, ϵ_min)` & [`StopWhenChangeLess`](@ref)`(1e-10))`) 停止するタイミングを示す [`StoppingCriterion`](@ref) から継承されたファンクタ。

制約の勾配の `range` に関しては、他のパワーマンフォールド接線空間表現、主に [`ArrayPowerRepresentation`](@extref Manifolds :jl:type:`Manifolds.ArrayPowerRepresentation`) を使用することができます。勾配がその表現でより効率的に計算できる場合です。

`equality_constraints` と `inequality_constraints` では、それぞれの `h` と `g` の範囲の次元を提供する必要があります。提供されない場合、`M` と開始点 `p0` とともに、これらのいずれかを呼び出して推測を試みます。

# 出力

得られた（近似的な）最小化点 $p^*$、詳細は [`get_solver_return`](@ref) を参照してください。 ```
