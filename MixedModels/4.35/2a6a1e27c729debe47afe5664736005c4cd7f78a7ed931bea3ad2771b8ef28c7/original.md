```
objective!(m::MixedModel, θ)
objective!(m::MixedModel)
```

Equivalent to `objective(updateL!(setθ!(m, θ)))`.

When `m` has a single, scalar random-effects term, `θ` can be a scalar.

The one-argument method curries and returns a single-argument function of `θ`.

Note that these methods modify `m`. The calling function is responsible for restoring the optimal `θ`.
