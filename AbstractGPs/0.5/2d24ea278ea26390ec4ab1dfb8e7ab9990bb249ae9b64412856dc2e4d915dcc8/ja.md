```
function update_posterior(
    f_post_approx::ApproxPosteriorGP{<:Union{VFE,DTC}},
    fx::FiniteGP,
    y::AbstractVector{<:Real}
)
```

新しい観測値のセットを考慮して `ApproxPosteriorGP` を更新します。ここでは、同じ擬似点のセットを保持します。
