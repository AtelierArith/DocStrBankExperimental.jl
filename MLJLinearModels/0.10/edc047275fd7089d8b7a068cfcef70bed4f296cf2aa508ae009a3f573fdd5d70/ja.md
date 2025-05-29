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

ハーバー回帰の目的：

$$
∑ρ(Xθ - y) + n⋅λ|θ|₂²/2 + n⋅γ|θ|₁
$$

ここで`ρ`はハーバー関数`ρ(r) = r²/2``if`|r|≤δ`and`ρ(r)=δ(|r|-δ/2)`otherwiseであり、``n``はサンプルの数`size(X, 1)`です。`scale*penalty*with_samples = false`の場合、目的関数は``∑ρ(Xθ - y) + λ|θ|₂²/2 + γ|θ|₁``です。
