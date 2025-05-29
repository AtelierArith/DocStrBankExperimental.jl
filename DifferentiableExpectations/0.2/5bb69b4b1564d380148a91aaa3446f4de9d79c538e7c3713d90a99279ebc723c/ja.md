```
Reparametrization{threaded} <: DifferentiableExpectation{threaded}
```

微分可能なパラメトリック期待値 `F : θ -> 𝔼[f(X)]` で、`X ∼ p(θ)` を再パラメータ化（またはパスワイズ）勾配推定器を使用して計算します：もし `X = g(Z,θ)` で `Z ∼ q` ならば

```
∂F(θ) = 𝔼_q[∂f(g(Z,θ)) ∂₂g(Z,θ)ᵀ]
```

# 例

```jldoctest
using DifferentiableExpectations, Distributions, Zygote

E = Reparametrization(exp, Normal; nb_samples=10^4)
E_true(μ, σ) = mean(LogNormal(μ, σ))

μ, σ = 0.5, 1,0
∇E, ∇E_true = gradient(E, μ, σ), gradient(E_true, μ, σ)
isapprox(collect(∇E), collect(∇E_true); rtol=1e-1)

# 出力

true
```

# コンストラクタ

```
Reparametrization(
    f,
    dist_constructor,
    rng=Random.default_rng(),
    nb_samples=1,
    threaded=false,
    seed=nothing
)
```

# フィールド

  * `f::Any`: 期待値内で適用される関数
  * `dist_constructor::Any`: 確率分布のコンストラクタ `(θ...) -> p(θ)`
  * `rng::Random.AbstractRNG`: 擬似乱数生成器
  * `nb_samples::Int64`: モンテカルロサンプルの数
  * `seed::Union{Nothing, Int64}`: 擬似乱数生成器のシード、各呼び出しの前にリセットされます。シードなしの場合は `nothing` に設定します。

# 参照

  * [`DifferentiableExpectation`](@ref)
