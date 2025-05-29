```
simulate!(rng::AbstractRNG, m::MixedModel{T}; β=fixef(m), σ=m.σ, θ=T[])
simulate!(m::MixedModel; β=fixef(m), σ=m.σ, θ=m.θ)
```

Overwrite the response (i.e. `m.trms[end]`) with a simulated response vector from model `m`.

This simulation includes sampling new values for the random effects.

`β` can be specified either as a pivoted, full rank coefficient vector (cf. [`fixef`](@ref)) or as an unpivoted full dimension coefficient vector (cf. [`coef`](@ref)), where the entries corresponding to redundant columns will be ignored.

!!! note
    Note that `simulate!` methods with a `y::AbstractVector` as the first argument (besides the RNG) and `simulate` methods return the simulated response. This is in contrast to `simulate!` methods with a `m::MixedModel` as the first argument, which modify the model's response and return the entire modified model.

