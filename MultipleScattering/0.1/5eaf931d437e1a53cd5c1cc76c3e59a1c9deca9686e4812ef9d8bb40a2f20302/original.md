See also: [`ContinuousImpulse`](@ref), [`frequency_to_time`](@ref), [`DiscreteGaussianImpulse`](@ref)

```
DiscreteImpulse{T<:AbstractFloat}
```

A struct used to represent a numerical impulse. Only the fields: `in_freq` which is the frequency response vector, and the frequency vector `ω` are required to use this struct to use in the function `frequency_to_time`.
