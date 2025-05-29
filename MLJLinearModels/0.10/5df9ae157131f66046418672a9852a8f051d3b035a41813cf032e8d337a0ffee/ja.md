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

最小絶対偏差回帰の目的：

$$
|Xθ - y|₁ + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁
$$

ここで $n$ はサンプルの数 `size(X, 1)` です。`scale_penalty_with_samples = false` の場合、目的関数は $|Xθ - y|₁ + λ|θ|₂²/2 + γ|θ|₁$ です。

これは `δ=0.5`（中央値）の特定のタイプの分位点回帰です。
