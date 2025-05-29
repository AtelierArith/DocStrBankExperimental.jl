```
Reinforce{threaded} <: DifferentiableExpectation{threaded}
```

微分可能なパラメトリック期待値 `F : θ -> 𝔼[f(X)]` で、`X ∼ p(θ)` を使用し、REINFORCE（またはスコア関数）勾配推定器を用います：

```
∂F(θ) = 𝔼[f(X) ∇₂logp(X,θ)ᵀ]
```

# 例

```jldoctest
using DifferentiableExpectations, Distributions, Zygote

E = Reinforce(exp, Normal; nb_samples=10^5)
E_true(μ, σ) = mean(LogNormal(μ, σ))

μ, σ = 0.5, 1,0
∇E, ∇E_true = gradient(E, μ, σ), gradient(E_true, μ, σ)
isapprox(collect(∇E), collect(∇E_true); rtol=1e-1)

# 出力

true
```

# コンストラクタ

```
Reinforce(
    f,
    dist_constructor,
    dist_logdensity_grad=nothing;
    rng=Random.default_rng(),
    nb_samples=1,
    threaded=false,
    seed=nothing
)
```

# フィールド

  * `f::Any`: 期待値内で適用される関数
  * `dist_constructor::Any`: 確率分布のコンストラクタ `(θ...) -> p(θ)`
  * `dist_logdensity_grad::Any`: `nothing` またはパラメータ勾配呼び出し可能 `(x, θ...) -> ∇₂logp(x, θ)`
  * `rng::Random.AbstractRNG`: 擬似乱数生成器
  * `nb_samples::Int64`: モンテカルロサンプルの数
  * `seed::Union{Nothing, Int64}`: 擬似乱数生成器のシード、各呼び出しの前にリセットされます。シードなしの場合は `nothing` に設定します。

# 参照

  * [`DifferentiableExpectation`](@ref)
