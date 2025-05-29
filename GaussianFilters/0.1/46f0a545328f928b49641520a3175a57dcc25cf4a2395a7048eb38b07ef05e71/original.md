```
measure(m::LinearObservationModel, x::AbstractVector{<:Number}, u::AbstractVector{<:Number})
measure(m::LinearObservationModel, x::AbstractVector{T}, u::AbstractVector{T}, rng::AbstractRNG) where T<:Number
```

Returns an observation of state x according to the linear observation model m, with control inputs u. If rng is passed, adds additive Gaussian noise to the observation.
