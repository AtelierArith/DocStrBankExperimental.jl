```julia
RobustRegression(; ...)
RobustRegression(ρ; ...)
RobustRegression(ρ, λ; ...)
RobustRegression(
    ρ,
    λ,
    γ;
    rho,
    lambda,
    gamma,
    penalty,
    fit_intercept,
    scale_penalty_with_samples,
    penalize_intercept
)

```

目的関数: $∑ρ(Xθ - y) + n⋅λ|θ|₂² + n⋅γ|θ|₁$ ここで、ρは残差に対する与えられた関数であり、$n$はサンプルの数 `size(X, 1)` です。`scale_penalty_with_samples = false` の場合、目的関数は $∑ρ(Xθ - y) + λ|θ|₂² + γ|θ|₁$ です。
