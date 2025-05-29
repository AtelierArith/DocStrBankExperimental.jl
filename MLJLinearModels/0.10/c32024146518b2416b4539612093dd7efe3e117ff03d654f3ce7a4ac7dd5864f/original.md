```julia
LogisticRegression(; ...)
LogisticRegression(λ; ...)
LogisticRegression(
    λ,
    γ;
    lambda,
    gamma,
    penalty,
    fit_intercept,
    penalize_intercept,
    scale_penalty_with_samples,
    multi_class,
    nclasses
)

```

Objective function: $L(y, Xθ) + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁$ where `L` is either the logistic loss in the binary case or the multinomial loss otherwise and $n$ is the number of samples `size(X, 1)`. With `scale_penalty_with_samples = false` the objective function is $L(y, Xθ) + λ|θ|₂²/2 + γ|θ|₁$.
