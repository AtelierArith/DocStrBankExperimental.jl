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

Objective function: $∑ρ(Xθ - y) + n⋅λ|θ|₂² + n⋅γ|θ|₁$ where ρ is a given function on the residuals and $n$ is the number of samples `size(X, 1)`. With `scale_penalty_with_samples = false` the objective function is $∑ρ(Xθ - y) + λ|θ|₂² + γ|θ|₁$.
