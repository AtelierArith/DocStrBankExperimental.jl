```julia
MultinomialRegression(a; kwa...)

```

目的関数: $L(y, Xθ) + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁$ ここで `L` は多項ロスであり、$n$ はサンプルの数 `size(X, 1)` です。`scale_penalty_with_samples = false` の場合、目的関数は $L(y, Xθ) + λ|θ|₂²/2 + γ|θ|₁$ です。
