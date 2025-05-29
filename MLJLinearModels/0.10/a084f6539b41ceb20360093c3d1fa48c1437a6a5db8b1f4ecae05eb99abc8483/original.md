```julia
ElasticNetRegression(; ...)
ElasticNetRegression(λ; ...)
ElasticNetRegression(
    λ,
    γ;
    lambda,
    gamma,
    fit_intercept,
    penalize_intercept,
    scale_penalty_with_samples
)

```

Objective function: $|Xθ - y|₂²/2 + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁$, where $n$ is the number of samples `size(X, 1)`. With `scale_penalty_with_samples = false` the objective function is $|Xθ - y|₂²/2 + λ|θ|₂²/2 + γ|θ|₁$
