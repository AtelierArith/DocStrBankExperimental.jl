```
FletcherPenaltyNLP(nlp, σ, hessian_approx, [x0 = nlp.meta.x0]; qds = LDLtSolver(nlp, S(0)))
FletcherPenaltyNLP(nlp, σ, ρ, δ, hessian_approx, [x0 = nlp.meta.x0]; qds = LDLtSolver(nlp, S(0)))
FletcherPenaltyNLP(nlp; σ_0 = 1, ρ_0 = 0, δ_0 = 0, hessian_approx = Val(2), x0 = nlp.meta.x0, qds = LDLtSolver(nlp, S(0)))
```

ここでは、最小化問題に対するFletcherの正確なペナルティ法の実装を考えます：

$$
    minₓ    f(x)    s.t.    c(x) = ℓ, l ≤ x ≤ u
$$

Fletcherペナルティ関数を使用して：

$$
    minₓ    f(x) - (c(x) - ℓ)^T ys(x) + 0.5 ρ ||c(x) - ℓ||²₂    s.t.    l ≤ x ≤ u
$$

ここで

$$
    ys(x)    ∈    arg min\_y    0.5 ||A(x)y - g(x)||²₂ + σ (c(x) - ℓ)^T y + 0.5 || δ ||²₂
$$

# 引数

  * `nlp::AbstractNLPModel`: 解かれるモデル、`NLPModels.jl`を参照；
  * `x::S`: 初期推定。`x`が指定されていない場合、`nlp.meta.x0`が使用されます；
  * `σ`, `ρ`, `δ` サブプロブレムのパラメータ；
  * `hessian_approx` ヘッセ行列の近似のために `Val(1)` または `Val(2)`；
  * `qds`: 線形代数計算のためのソルバ構造、[`LDLtSolver`](@ref) または [`IterativeSolver`](@ref)を参照。

# 注意：

  * `obj`、`grad`、`objgrad` 関数の評価は、元の `nlp` から関数を評価します。これらの値は `fx`、`cx`、`gx` に格納されます。
  * ペナルティベクトル `ys` の値も格納されます。
  * ヘッセ行列の構造は密です。

# 例

```julia
julia> using FletcherPenaltySolver, ADNLPModels
julia> nlp = ADNLPModel(x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0])
julia> fp_sos  = FletcherPenaltyNLP(nlp)
```
