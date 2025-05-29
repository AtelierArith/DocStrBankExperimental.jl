```julia
QuantileRegression(; ...)
QuantileRegression(δ; ...)
QuantileRegression(δ, λ; ...)
QuantileRegression(
    δ,
    λ,
    γ;
    delta,
    lambda,
    gamma,
    penalty,
    fit_intercept,
    scale_penalty_with_samples,
    penalize_intercept
)

```

目的を持つ分位回帰:

$$
∑ρ(Xθ - y) + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁
$$

ここで `ρ` はチェック関数 `ρ(r) = r(δ - 1(r < 0))` であり、$n$ はサンプルの数 `size(X, 1)` です。`scale_penalty_with_samples = false` の場合、目的関数は $∑ρ(Xθ - y) + λ|θ|₂²/2 + γ|θ|₁$ です。
