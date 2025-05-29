```julia
MultinomialRegression(a; kwa...)

```

Objective function: $L(y, Xθ) + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁$ where `L` is the multinomial loss and $n$ is the number of samples `size(X, 1)`. With `scale_penalty_with_samples = false` the objective function is $L(y, Xθ) + λ|θ|₂²/2 + γ|θ|₁$.
