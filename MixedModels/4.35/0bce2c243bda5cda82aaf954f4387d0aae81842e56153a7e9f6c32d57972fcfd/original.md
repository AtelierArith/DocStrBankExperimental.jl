```
simulate!([rng::AbstractRNG,] y::AbstractVector, m::MixedModel{T}[, newdata];
                β = coef(m), σ = m.σ, θ = T[], wts=m.wts)
simulate([rng::AbstractRNG,] m::MixedModel{T}[, newdata];
                β = coef(m), σ = m.σ, θ = T[], wts=m.wts)
```

Simulate a new response vector, optionally overwriting a pre-allocated vector.

New data can be optionally provided in tabular format.

This simulation includes sampling new values for the random effects. Thus in contrast to `predict`, there is no distinction in between "new" and "old" / previously observed random-effects levels.

Unlike `predict`, there is no `type` parameter for `GeneralizedLinearMixedModel` because the noise term in the model and simulation is always on the response scale.

The `wts` argument is currently ignored except for `GeneralizedLinearMixedModel` models with a `Binomial` distribution.

!!! note
    Note that `simulate!` methods with a `y::AbstractVector` as the first argument (besides the RNG) and `simulate` methods return the simulated response. This is in contrast to `simulate!` methods with a `m::MixedModel` as the first argument, which modify the model's response and return the entire modified model.

