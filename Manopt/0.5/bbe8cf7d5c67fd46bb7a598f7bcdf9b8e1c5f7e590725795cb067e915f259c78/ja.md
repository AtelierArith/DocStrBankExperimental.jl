```
augmented_Lagrangian_method(M, f, grad_f, p=rand(M); kwargs...)
augmented_Lagrangian_method(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
augmented_Lagrangian_method!(M, f, grad_f, p; kwargs...)
augmented_Lagrangian_method!(M, cmo::ConstrainedManifoldObjective, p; kwargs...)
```

拡張ラグランジュ法 (ALM) [LiuBoumal:2019](@cite) を実行します。この方法は `p` のインプレースで動作することができます。

ALMの目的は、制約付き最適化タスクの解を見つけることです。

$$
\begin{aligned}
\operatorname*{arg\,min}_{p ∈ \mathcal M} & f(p)\\
\text{subject to}\quad&g_i(p) ≤ 0 \quad \text{ for } i= 1, …, m,\\
\quad & h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

ここで `M` はリーマン多様体であり、$f$、$\{g_i\}_{i=1}^{n}$ および $\{h_j\}_{j=1}^{m}$ は `M` から ℝ への2回連続微分可能な関数です。アルゴリズムの各ステップ $k$ では、[`AugmentedLagrangianCost`](@ref)  $\mathcal L_{ρ^{(k)}}(p, μ^{(k)}, λ^{(k)})$ が \mathcal M 上で最小化されます。ここで、$μ^{(k)} ∈ ℝ^n$ および $λ^{(k)} ∈ ℝ^m$ はラグランジュ乗数の現在の反復値であり、$ρ^{(k)}$ は現在のペナルティパラメータです。

次に、ラグランジュ乗数は次のように更新されます。

$$
λ_j^{(k+1)} =\operatorname{clip}_{[λ_{\min},λ_{\max}]} (λ_j^{(k)} + ρ^{(k)} h_j(p^{(k+1)})) \text{for all} j=1,…,p,
$$

および

$$
μ_i^{(k+1)} =\operatorname{clip}_{[0,μ_{\max}]} (μ_i^{(k)} + ρ^{(k)} g_i(p^{(k+1)})) \text{ for all } i=1,…,m,
$$

ここで、$λ_{\text{min}} ≤ λ_{\text{max}}$ および $μ_{\text{max}}$ は乗数の境界です。

次に、精度許容値 $ϵ$ は次のように更新されます。

$$
ϵ^{(k)}=\max\{ϵ_{\min}, θ_ϵ ϵ^{(k-1)}\},
$$

ここで、$ϵ_{\text{min}}$ は $ϵ$ が許可される最小値であり、$θ_ϵ ∈ (0,1)$ は定数スケーリングファクターです。

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

ここで、$θ_ρ ∈ (0,1)$ は定数スケーリングファクターです。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `grad_f`: 関数 `(M, p) -> X` または `(M, X, p) -> X` として、$f$ の (リーマン) 勾配 $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ を計算する関数

# オプション ([`ConstrainedManifoldObjective`](@ref) `cmo` で呼び出されない場合)

  * `g=nothing`: 不等式制約
  * `h=nothing`: 等式制約
  * `grad_g=nothing`: 不等式制約の勾配
  * `grad_h=nothing`: 等式制約の勾配

`(`g`,`grad*g`)` または `(`h`,`grad*h`)` のいずれかのペアを提供する必要があります。そうでない場合、問題は制約されておらず、より良いソルバーは例えば [`quasi_Newton`](@ref) です。

# キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが結果を割り当てるか、入力引数を修正してその中で結果を返すかを指定します（[`AllocatingEvaluation`](@ref) または [`InplaceEvaluation`](@ref)）。通常、最初の引数は多様体であるため、修正された引数は2番目の引数です。
  * `ϵ=1e-3`:           精度許容値
  * `ϵ_min=1e-6`:       精度許容値の下限
  * `ϵ_exponent=1/100`: ϵ 更新ファクターの指数; また、アルゴリズムが自然に終了するまでの最大精度が必要な反復回数の逆数

      * `equality_constraints=nothing`: 等式制約の数 $n$。

    提供されない場合、`g` の勾配を呼び出してこれを推定します。
  * `gradient_range=nothing`: 制約の両方の勾配がどのように表現されるかを指定
  * `gradient_equality_range=gradient_range`:  等式制約の勾配がどのように表現されるかを指定、[`VectorGradientFunction`](@ref) を参照。
  * `gradient_inequality_range=gradient_range`: 不等式制約の勾配がどのように表現されるかを指定、[`VectorGradientFunction`](@ref) を参照。
  * `inequality_constraints=nothing`: 不等式制約の数 $m$。提供されない場合、`g` の勾配を呼び出してこれを推定します。
  * `λ=ones(size(h(M,x),1))`: 等式制約に関するラグランジュ乗数
  * `λ_max=20.0`:       等式制約に属するラグランジュ乗数の上限
  * `λ_min=- λ_max`:    等式制約に属するラグランジュ乗数の下限
  * `μ=ones(size(h(M,x),1))`: 不等式制約に関するラグランジュ乗数
  * `μ_max=20.0`: 不等式制約に属するラグランジュ乗数の上限
  * `ρ=1.0`:            ペナルティパラメータ
  * `τ=0.8`:            ペナルティパラメータの評価改善のためのファクター
  * `θ_ρ=0.3`:          ペナルティパラメータのスケーリングファクター
  * `θ_ϵ=(ϵ_min / ϵ)^(ϵ_exponent)`: 正確さのスケーリングファクター
  * `sub_cost=[`AugmentedLagrangianCost± (@ref)`(cmo, ρ, μ, λ):` 拡張ラグランジュコストを使用し、提供された関数から構築された [`ConstrainedManifoldObjective`](@ref) に基づきます。これは `sub_problem=` キーワードを定義するために使用され、`sub_problem` を直接設定した場合には影響しません。
  * `sub_grad=[`AugmentedLagrangianGrad`](@ref)`(cmo, ρ, μ, λ)`: 拡張ラグランジュ勾配を使用し、提供された関数から構築された [`ConstrainedManifoldObjective`](@ref) に基づきます。これは`sub*problem=`キーワードを定義するために使用され、`sub*problem` を直接設定した場合には影響しません。
  * `sub_kwargs=``(;)`: サブソルバーの目的の [`decorate_objective!`](@ref)、サブソルバーの状態の [`decorate_state!`](@ref)、およびサブ状態コンストラクタ自体に渡されるキーワード引数の名前付きタプル。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)([`StopWhenSmallerOrEqual`](@ref)`(:ϵ, ϵ_min)`[`&`](@ref StopWhenAll)[`StopWhenChangeLess`](@ref)`(1e-10) )`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`: 停止基準が満たされていることを示すファンクタ
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`: ソルバーの問題または閉じた形式の解関数を指定します。これは割り当て可能またはインプレースである可能性があります。
  * `sub_state=`[`QuasiNewtonState`](@ref): 使用するサブソルバーを指定する状態。閉じた形式の解の場合、これは関数のタイプを示します。準ニュートン法の場合、[`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) と [`InverseBFGS`](@ref) が使用されます。
  * `sub_stopping_criterion::StoppingCriterion=`[`StopAfterIteration`](@ref)`(300)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(ϵ)`[`|`](@ref StopWhenAny)[`StopWhenStepsizeLess`](@ref)`(1e-8)`,

制約の勾配の `range` に関しては、他のパワー多様体接空間表現、主に [`ArrayPowerRepresentation`](@extref Manifolds :jl:type:`Manifolds.ArrayPowerRepresentation`) が使用される場合があります。勾配がその表現でより効率的に計算できる場合です。

他のすべてのキーワード引数は、状態デコレーターのために [`decorate_state!`](@ref) に、目的デコレーターのために [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、[`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードに注意してください。 ```
