```julia
LADRegression(; ...)
LADRegression(λ; ...)
LADRegression(
    λ,
    γ;
    lambda,
    gamma,
    penalty,
    scale_penalty_with_samples,
    fit_intercept,
    penalize_intercept
)

```

Least Absolute Deviation regression with objective:

$|Xθ - y|₁ + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁$ where $n$ is the number of samples `size(X, 1)`. With `scale_penalty_with_samples = false` the objective function is $|Xθ - y|₁ + λ|θ|₂²/2 + γ|θ|₁$.

This is a specific type of Quantile Regression with `δ=0.5` (median).
