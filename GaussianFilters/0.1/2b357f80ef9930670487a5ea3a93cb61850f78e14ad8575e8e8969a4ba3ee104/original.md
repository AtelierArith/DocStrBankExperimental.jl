```
predict(m::LinearDynamicsModel, x::AbstractVector{<:Number}, u::AbstractVector{<:Number})
predict(m::LinearDynamicsModel, x::AbstractVector{<:Number}, u::AbstractVector{<:Number}, rng::AbstractRNG)
```

Uses the linear dynamics model to propagate the state x one step forward in time with control input u. If rng is given, it adds process noise. 
