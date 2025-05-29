```
sample([rng::AbstractRNG], model::StateSpaceModel, T::Integer; kwargs...)
```

Simulate a trajectory of length `T` from the state space model.

Returns a tuple `(x0, xs, ys)` where `x0` is the initial state, `xs` is a vector of latent states, and `ys` is a vector of observations.
