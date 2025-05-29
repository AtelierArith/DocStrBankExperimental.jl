```
function update_posterior(
    f_post_approx::ApproxPosteriorGP{<:Union{VFE,DTC}},
    fx::FiniteGP,
    y::AbstractVector{<:Real}
)
```

Update the `ApproxPosteriorGP` given a new set of observations. Here, we retain the same  set of pseudo-points.
