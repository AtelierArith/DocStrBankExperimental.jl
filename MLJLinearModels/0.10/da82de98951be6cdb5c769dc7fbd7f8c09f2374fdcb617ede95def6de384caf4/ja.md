```julia
RidgeRegression(; ...)
RidgeRegression(
    λ;
    lambda,
    fit_intercept,
    penalize_intercept,
    scale_penalty_with_samples
)

```

目的関数: $|Xθ - y|₂²/2 + n⋅λ|θ|₂²/2$、ここで $n$ はサンプルの数 `size(X, 1)` です。`scale_penalty_with_samples = false` の場合、目的関数は $|Xθ - y|₂²/2 + λ|θ|₂²/2$ です。
