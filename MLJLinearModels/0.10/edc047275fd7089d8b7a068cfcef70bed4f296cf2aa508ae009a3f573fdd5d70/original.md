```julia
HuberRegression(; ...)
HuberRegression(δ; ...)
HuberRegression(δ, λ; ...)
HuberRegression(
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

Huber Regression with objective:

$∑ρ(Xθ - y) + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁$

Where `ρ` is the Huber function `ρ(r) = r²/2``if`|r|≤δ`and`ρ(r)=δ(|r|-δ/2)`otherwise and``n``is the number of samples`size(X, 1)`. With`scale*penalty*with_samples = false`the objective function is``∑ρ(Xθ - y) + λ|θ|₂²/2 + γ|θ|₁``.
