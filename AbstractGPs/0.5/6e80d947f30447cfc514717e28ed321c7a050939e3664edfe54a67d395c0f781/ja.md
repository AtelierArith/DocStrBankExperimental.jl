```
function update_posterior(
    f_post_approx::ApproxPosteriorGP{<:Union{VFE,DTC}},
    z::FiniteGP,
)
```

既存の擬似点のセットに追加する新しい擬似点のセットを考慮して、`ApproxPosteriorGP`を更新します。
