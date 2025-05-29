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

Quantile Regression with objective:

$∑ρ(Xθ - y) + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁$

Where `ρ` is the check function `ρ(r) = r(δ - 1(r < 0))` and $n$ is the number of samples `size(X, 1)`. With `scale_penalty_with_samples = false` the objective function is $∑ρ(Xθ - y) + λ|θ|₂²/2 + γ|θ|₁$.
