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

目的関数: $L(y, Xθ) + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁$ ここで `L` は二項の場合のロジスティック損失またはそれ以外の場合の多項損失であり、$n$ はサンプルの数 `size(X, 1)` です。`scale_penalty_with_samples = false` の場合、目的関数は $L(y, Xθ) + λ|θ|₂²/2 + γ|θ|₁$ です。
