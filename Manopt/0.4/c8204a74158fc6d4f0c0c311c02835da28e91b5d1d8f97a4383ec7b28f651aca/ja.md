```
ConstrainedManifoldObjective{T<:AbstractEvaluationType, C<:ConstraintType} <: AbstractManifoldObjective{T}
```

制約付き目的関数を説明します

$$
\begin{aligned}
 \operatorname*{arg\,min}_{p ∈\mathcal{M}} & f(p)\\
 \text{subject to } &g_i(p)\leq0 \quad \text{ for all } i=1,…,m,\\
 \quad &h_j(p)=0 \quad \text{ for all } j=1,…,n.
\end{aligned}
$$

# フィールド

  * `objective`: 制約のない目的関数を表す [`AbstractManifoldObjective`](@ref) で、コスト $f$、コスト $f$ の勾配、そして場合によってはヘッセ行列を含みます。
  * `equality_constraints`: 等式制約を表す [`AbstractManifoldObjective`](@ref)

$$
h: \mathcal M → \mathbb R^n
$$

もその勾配および/またはヘッセ行列を含む可能性があります。

  * `equality_constraints`: 等式制約を表す [`AbstractManifoldObjective`](@ref)

$$
h: \mathcal M → \mathbb R^n
$$

もその勾配および/またはヘッセ行列を含む可能性があります。

# コンストラクタ

```
ConstrainedManifoldObjective(M::AbstractManifold, f, grad_f;
    g=nothing,
    grad_g=nothing,
    h=nothing,
    grad_h=nothing;
    hess_f=nothing,
    hess_g=nothing,
    hess_h=nothing,
    equality_constraints=nothing,
    inequality_constraints=nothing,
    evaluation=AllocatingEvaluation(),
    M = nothing,
    p = isnothing(M) ? nothing : rand(M),
)
```

関与するすべての単一関数 `f`, `grad_f`, `g`, `grad_g`, `h`, `grad_h` に基づいて制約付き目的関数を生成します。これらの各関数に対してヘッセ行列をオプションで提供することもできます。`equality_constraints` と `inequality_constraints` には、それぞれの `h` と `g` の範囲の次元を提供する必要があります。また、制約の評価を自動的に試みるために、マニフォールド `M` と点 `p` を提供することもできます。

```
ConstrainedManifoldObjective(M::AbstractManifold, mho::AbstractManifoldObjective;
    equality_constraints = nothing,
    inequality_constraints = nothing
)
```

明示的な制約 $g$ と $h$、およびそれらの勾配を持つ制約付き目的関数を生成するか、これらがすでに [`VectorGradientFunction`](@ref) にカプセル化されている形式で生成します。

どちらのバリアントも、少なくとも1つの制約（およびその勾配）が提供される必要があります。3つの部分のいずれかがヘッセ行列を提供する場合、対応するオブジェクト、すなわち `f` のための [`ManifoldHessianObjective`](@ref) または `g` または `h` のための [`VectorHessianFunction`](@ref) が作成されます。
