```
function update_posterior(
    f_post_approx::ApproxPosteriorGP{<:Union{VFE,DTC}},
    z::FiniteGP,
)
```

Update the `ApproxPosteriorGP` given a new set of pseudo-points to append to the existing  set of pseudo-points.
